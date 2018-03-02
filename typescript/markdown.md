# 1. 개요
## 1.1. 개요
### 1.1.1. 줄 내림
미나어리ㅏㅁ너이럼니ㅓㅇ리ㅏㅓㅁㄴ이ㅓ리ㅏㅁ넝리ㅏㅓㄴ미ㅏ어리ㅓ  
ㄴㅁㅇ라ㅓㅁ니아ㅓㄹ
미나어린멍리ㅏㅓㅁ닝러ㅣ마넝리`ㅓㅁ니`ㅏ아ㅓ리ㅏㅓㅁㄴ이ㅏ러ㅣㅏㅁ넝리  
ㅏㅓㅁ니아ㅓ리ㅏ멀
ㅣ마넝리ㅏㅓㄴㅁ이러ㅣㅏㅁ넝리ㅏ__ㅓㅁㄴ이__ㅏㅓ리먼이러미나ㅓㅇ리ㅏㅓ  
ㅁ니아ㅓ리ㅓㅁㄴ이라ㅓ
미나어리ㅏㅓㄴㅁ이라ㅓ미ㅏㄴ어ㅣ_러민어_리ㅏㅓㅁㄴ이ㅏㅓ라미ㅓ  
ㄴ이럼아ㅣ널

[test](#3.3)

### 1.1.2
# 2. 폰트 스타일
## 2.1 볼드, 이태릭
### 2.1.1. 볼드
 __이 문자는 볼드 스타일이 적용된 문자열입니다.__
### 2.1.2. 이태릭
 _이 문자는 이태릭 스타일이 적용된 문자열입니다._
### 3.1.3. 볼드 + 이태릭
 ___이 문자는 이태릭 스타일이 적용된 문자열입니다.___
## 2.2 하이라이트
 `이 문자는 적용된 문자열 입니다.`
### 2.2.1
### 2.2.2
# 3. 인용구문
## 3.3
이 내용은 네이버 XXXX 블로그에서 인용한 내용입니다.
> _네이버 블로그_ - [http://blog.naver.com](http://blog.naver.com)  
> alskjdlfkjsd  
> alsdkjfldsjf

# 4. 하이퍼링크
이[링크](http://www.naver.com)는 naver로 이동합니다.

# 5. 이미지, 아이콘 삽입.
![이미지](https://i.stack.imgur.com/Xn4c0.png)

# 표.
|컬럼1|컬럼2|컬럼3|
|:---|---:|---:|
|11|22|33|
|11|22|33|
|11|22|33|
|11|22|33|

# 텍스트 블록
```
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
	name : "TelFormatter"
})
/**
 * TelFormatter Pipe.
 * Templates에서 전화번호를 `전화번호 리터럴` 형태로 변환.
 * @author Arom IT Inc.
 * @version 1.0
 */
export class TelFormatter implements PipeTransform {
	/**
	 * 전화번호 9 ~ 12자리 문자열을 `전화번호 리터럴`로 변환.
	 * <ul>
	 * <li> ##-###-####</li>
	 * <li> ##-####-####</li>
	 * <li> ###-###-####</li>
	 * <li> ###-####-####</li>
	 * <li> ####-####-####</li></ul>
	 * @access public
	 * @param {string} value 전화번호 문자열.
	 * @version 1.0
	 */
	transform(value){
		if(!value){
			return "";
		}
		let len = value.length;
		let ret = value;
		if(len == 9){
			ret = value.substring(0, 2);
			ret += '-';
			ret += value.substring(2, 5);
			ret += '-';
			ret += value.substring(5, 9);
		}else if(len == 10) {
			ret = value.substring(0, 3);
			ret += '-';
			ret += value.substring(3, 6);
			ret += '-';
			ret += value.substring(6, 10);
		}else if(len == 11) {
			ret = value.substring(0, 3);
			ret += '-';
			ret += value.substring(3, 7);
			ret += '-';
			ret += value.substring(7, 11);
		}else if(len == 12) {
			ret = value.substring(0, 4);
			ret += '-';
			ret += value.substring(4, 8);
			ret += '-';
			ret += value.substring(8, 12);
		}
		else{
			console.log('[TelFormatter] invalid tel literal : ', value);
		}

		return ret;
	}
}

```

```JavaScript
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
	name : "TelFormatter"
})
/**
 * TelFormatter Pipe.
 * Templates에서 전화번호를 `전화번호 리터럴` 형태로 변환.
 * @author Arom IT Inc.
 * @version 1.0
 */
export class TelFormatter implements PipeTransform {
	/**
	 * 전화번호 9 ~ 12자리 문자열을 `전화번호 리터럴`로 변환.
	 * <ul>
	 * <li> ##-###-####</li>
	 * <li> ##-####-####</li>
	 * <li> ###-###-####</li>
	 * <li> ###-####-####</li>
	 * <li> ####-####-####</li></ul>
	 * @access public
	 * @param {string} value 전화번호 문자열.
	 * @version 1.0
	 */
	transform(value){
		if(!value){
			return "";
		}
		let len = value.length;
		let ret = value;
		if(len == 9){
			ret = value.substring(0, 2);
			ret += '-';
			ret += value.substring(2, 5);
			ret += '-';
			ret += value.substring(5, 9);
		}else if(len == 10) {
			ret = value.substring(0, 3);
			ret += '-';
			ret += value.substring(3, 6);
			ret += '-';
			ret += value.substring(6, 10);
		}else if(len == 11) {
			ret = value.substring(0, 3);
			ret += '-';
			ret += value.substring(3, 7);
			ret += '-';
			ret += value.substring(7, 11);
		}else if(len == 12) {
			ret = value.substring(0, 4);
			ret += '-';
			ret += value.substring(4, 8);
			ret += '-';
			ret += value.substring(8, 12);
		}
		else{
			console.log('[TelFormatter] invalid tel literal : ', value);
		}

		return ret;
	}
}

```


# ul
- asdf
- adsfsdafasdf
- asdfsdaf

# ol

1. ddd
2. asd
3. aaa
