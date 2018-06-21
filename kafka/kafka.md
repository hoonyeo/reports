# KAFKA
## KAFKA란?
 Apache의 분산 스트리밍 플랫폼(Distributed Streaming Flatform).
 > *Streaming Flatform* 의 3가지 핵심기능  
 > 1. 메시지 큐 또는 Enterprize Messaging 시스템과 같은 **Stream의 생산 및 구독**.
 > 2. Stream의 **지속적인 저장**.
 > 3. Stream 발생 시 이를 처리.

## KAFKA의 네 가지 Core API
 1. Producer API : 하나 이상의 토픽을 생산.
 1. Consumer API : 하나 이상의 토픽을 구독 및 처리.
 1. Stream API : 특정 응용프로그램을 하나 이상의 토픽 생산, 구독이 가능.
 1. Connector API : 기존 응용프로그램 또는 데이터베이스 시스템을 연동하여 재사용 가능한 생산 및 구독 기능 제공.  
 ex) Database Connector를 이용하면 모든 테이블의 데이터가 변경사항 캡쳐가 가능.
