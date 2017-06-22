# Bluetooth
이 문서는 [블로그](https://zoyi.co/tech-blog/2015/11/03/Bluetoot-Low-Energy-BLE-%ED%8C%8C%ED%97%A4%EC%B9%98%EA%B8%B0/)를 인용하여 작성하였습니다.
## 블루투스란?
 1994년에 에릭슨이 최초로 개발한 개인 근거리 무선 통신을 위한 산업 표준으로 1999년 5월 20일에 공식적으로 발표.  
 마스터, 슬레이브 관계를 형성하여 통신하는 `Bluetooth Classic` 방식으로 상호 통신.

## Bluetooth의 두 가지 특성
규격의 가장 일반적인 구현 두 가지는 버전 2.0/2.1로 도입된 Bluetooth 기본 전송률/고급 데이터 전송률(BR/EDR) 및 버전 4.0/4.1/4.2로 도입된 저 에너지 Bluetooth(LE) 입니다.

### 차이점
<li>Bluetooth BR/EDR : 비교적 근거리의 지속적인 무선 연결을 설정하여 스트리밍 오디오 등의 사용에 이상적입니다.
</li>
<li>Bluetooth LE : 장거리 라디오 연결을 위한 쇼트 버스트를 가능하게 해서 지속적인 연결은 필요치 않지만 장시간의 배터리 수명에 의존하는 사물 인터넷(IoT) 애플리케이션에 이상적입니다.’
</li>
<li>듀얼 모드 : 듀얼 모드 칩셋은 BR/EDR 디바이스(오디오 헤드셋 등) 및 LE 디바이스(웨어러블 또는 리테일 비콘 등)에 모두 연결할 필요가 있는 스마트 전화 또는 테블릿 등의 단일 디바이스를 지원하기 위해 사용 가능합니다.
</li>



## BLE (Bluetooth Low Energy)란?
2010년 Bluetooth 4.0 규격이 발표되면서 기존 `Bluetooth Classic` 방식의 단점인 높은 베터리소모량 문제를 개선. `Bluetooth Smart Ready`, `Bluetooth Smart`등의 신규기술이 포함된 Bluetooth 4.0 이후 규격 및 기기들을 BLE(Bluetooth Low Energy)라 통칭.


### Bluetooth Smart, Bluetooth Smart Ready
BLE 기술이 등장하면서 다음의 3종류의 기기로 분류.

![그림1.BLE장치분류](https://zoyi.co/images/tech-blog/BLE/2015-11-02-BLE-ble-3-category.png)

#### Bluetooth Smart
디바이스 내에 있는 라디오는 “싱글모드” 라디오라 불리는데, BLE 연결만을 지원한다는 의미이다. 이들은 기존의 Bluetooth Classic 디바이스들과 호환이 되지 않고 듀얼모드 라디오를 가진 Bluetooth Smart Ready 디바이스 혹은 제조업체에 의해 호환성이 명시된 특정 Bluetooth 디바이스에만 연결이 가능하다. Bluetooth Smart 디바이스들은 ‘우리 집의 창문은 모두 잠겨 있는지’, ‘내 인슐린 농도는 얼마인지’, ‘오늘 내 몸무게는 몇 킬로그램인지’ 등과 같이 특정한 형태의 정보를 수집해, Bluetooth Smart Ready 디바이스로 보내기 위해 만들어진 디바이스이다. 종류에는 심박 모니터, 스마트 손목시계, 창문 및 현관 보안 센서, 자동차 키 체인, 그리고 혈압 팔찌 등이 있다.

#### Bluetooth Smart Ready
디바이스는 Bluetooth Classic 및 저에너지 Bluetooth 무선통신 (BLE)을 지원하기 때문에 “듀얼 모드” 라디오라고 불린다. 따라서, 이들은 현재 시장에 나와 있는 수억 종의 Bluetooth 디바이스들에 대한 역방향 호환성을 가진다. 종류에는 스마트폰, 태블릿, PC, TV 그리고 셋탑박스 및 게임 콘솔 등이 있다. 이런 디바이스들은 클래식 Bluetooth 디바이스 및 Bluetooth Smart 디바이스들로부터 데이터를 받아, 이들을 유용한 정보로 변환시키는 Bluetooth 시스템의 허브라고 할 수 있다.

## BLE 통신방식
BLE를 지원하는 디바이스들은 기본적으로 Advertise(Broadcast) 과 Connection 이라는 방법 통신

### Advertise Mode(Boradcast Mode)
특정 디바이스를 지정하지 않고 주변의 모든 디바이스에게 Signal을 보낸다. 다시 말해, 주변에 디바이스가 있건 없건, 다른 디바이스가 Signal을 듣는 상태이건 아니건, 자신의 Signal을 일방적으로 보내는 것.   
이 때, `Advertising type`의 Signal을 일정 주기로 보내게 된다. `1:n` 방식가능 (단, 단방향).

> Advertising type : 보완필요.

#### Central (Master)
 Central 디바이스는 다른 디바이스와 Connection을 맺기 위해, Connectable Advertising Signal을 주기적으로 스캔하다가, 적절한 디바이스에 연결을 요청한다. 연결이 되고 나면, Central 디바이스는 timing을 설정하고 주기적인 데이터 교환을 주도한다. 여기서 timing이란, 두 디바이스가 매번 같은 Channel에서 데이터를 주고 받기 위해 정하는 hopping 규칙이라고 생각하면 된다.

#### Peripheral (Slave)
Peripheral 디바이스는 다른 디바이스와 Connection을 맺기 위해, Connectable Advertising Signal을 주기적으로 보낸다. 이를 수신한 Central 디바이스가 Connection Request를 보내면, 이를 수락하여 Connecion을 맺는다. Connection을 맺고 나면 Central 디바이스가 지정한 timing에 맞추어 Channel을 같이 hopping을 하면서 주기적으로 데이터를 교환한다.

### Connection Mode
양방향으로 데이터를 주고받거나, Advertising Packet으로만 전달하기에는 많은 양의 데이터를 주고 받아야 하는 경우에는, `Connection Mode`로 통신을 한다. `1:1` 방식으로 디바이스 간에 데이터 교환이 일어난다.
