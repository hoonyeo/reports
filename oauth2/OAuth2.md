# OAuth2.0

## 1. About OAuth 2.0
OAuth 2.0 is the industry-standard protocol for authorization. OAuth 2.0 supersedes the work done on the original OAuth protocol created in 2006. OAuth 2.0 focuses on client developer simplicity while providing specific authorization flows for web applications, desktop applications, mobile phones, and living room devices. This specification is being developed within the [IETF OAuth WG](https://www.ietf.org/mailman/listinfo/oauth).
## 2. The difference with OAuth.
<li>
<b>More OAuth Flows to allow better support for non-browser based applications.</b> This is a main criticism against OAuth from client applications that were not browser based. For example, in OAuth 1.0, desktop applications or mobile phone applications had to direct the user to open their browser to the desired service, authenticate with the service, and copy the token from the service back to the application. The main criticism here is against the user experience. With OAuth 2.0, there are now new ways for an application to get authorization for a user.</li>  
<li>
<b>OAuth 2.0 no longer requires client applications to have cryptography.</b> This hearkens back to the old Twitter Auth API, which didn't require the application to HMAC hash tokens and request strings. With OAuth 2.0, the application can make a request using only the issued token over HTTPS.</li>  
<li>
<b>OAuth 2.0 signatures are much less complicated.</b> No more special parsing, sorting, or encoding.</li>  
<li>
<b>OAuth 2.0 Access tokens are "short-lived".</b> Typically, OAuth 1.0 Access tokens could be stored for a year or more (Twitter never let them expire). OAuth 2.0 has the notion of refresh tokens. While I'm not entirely sure what these are, my guess is that your access tokens can be short lived (i.e. session based) while your refresh tokens can be "life time". You'd use a refresh token to acquire a new access token rather than have the user re-authorize your application.</li>  
<li>
<b>Finally, OAuth 2.0 is meant to have a clean separation of roles between the server responsible for handling OAuth requests and the server handling user authorization.</b></li>  
<li>The diagram about difference between OAuth and OAuth2.

OAuth
![flow diagram OAuth](https://i.stack.imgur.com/UmvA7.png)

OAuth2
![flow diagram OAuth2](https://i.stack.imgur.com/Xn4c0.png)
</li>  

## 3. Roles.
OAuth2는 다음의 4가지 역할로 구성된다.

<li><b>resource owner</b>  
보호된 리소스에 접근할 수 있는 Entity. resource owner 는 end-user라고 한다.</li>  
<li><b>resource server</b>  
보호된 리소스에 대해 access token을 이용한 인가된 접근 및 응답을 제공하는 서버.</li>  
<li><b>client</b>  
리소스 소유자를 대신하여 권한을 가진 보호 된 리소스 요청을하는 응용 프로그램.
The term "client" does not imply any particular implementation characteristics (e.g., whether the application executes on a server, a desktop, or other devices).</li>  
<li><b>authorization server</b>
인증과 권한을 획득한 client에 access token을 발급하는 서버.
</li>

## 4. Protocol Flow.
Protocol Flow

     +--------+                               +---------------+
     |        |--(A)- Authorization Request ->|   Resource    |
     |        |                               |     Owner     |
     |        |<-(B)-- Authorization Grant ---|               |
     |        |                               +---------------+
     |        |
     |        |                               +---------------+
     |        |--(C)-- Authorization Grant -->| Authorization |
     | Client |                               |     Server    |
     |        |<-(D)----- Access Token -------|               |
     |        |                               +---------------+
     |        |
     |        |                               +---------------+
     |        |--(E)----- Access Token ------>|    Resource   |
     |        |                               |     Server    |
     |        |<-(F)--- Protected Resource ---|               |
     +--------+                               +---------------+

## 4. Authorization Grant
<li><b>Authorization Code</b>  
Authorization Request, Authorization Grant 과정을 Authorization Server를 통해 수행.</li>  
<li><b>Implicit</b>  
Authorization Code 방식에서 client 를 Browser 및 Javascript로 구현할 수 있도록 최적화 한 방식.
이 방식에서는 Authorization Code 방식과 달리 access token을 client가 직접 발급.</li>  
<li><b>Resource Owner Password Credentials</b>  
이 방식은 2-legged 방식의 인증이다. Client에 아이디/패스워드를 저장해 놓고 아이디/패스워드로 직접 access token을 받아오는 방식이다. Client 를 믿을 수 없을 때에는 사용하기에 위험하기 때문에 API 서비스의 공식 어플리케이션이나 믿을 수 있는 Client에 한해서만 사용하는 것을 추천한다.
로그인시에 API에 POST로 grant_type=password 라고 넘긴다.</li>  
<li><b>Client Credentials</b>  
어플리케이션 이 Confidential Client일 때 id와 secret을 가지고 인증하는 방식이다.
로그인시에 API에 POST로 grant_type=client_credentials 라고 넘긴다.
</li>  

## 5. OAuth 2.0 Provider.
### 5.1. Authorization Service.
### 5.2. Resource Service.
