additional-providers
====================

hybridauth providers for Kakao and Naver

PHP 를 사용해 웹싸이트를 만들때, 카카오톡 로그인 또는 네이버 로그인 구현하는 OAuth2 클라이언트. hybridauth 패키지를 설치한 뒤에, 사용할 수 있습니다.

How to use
----------

Just copy the files into `{project-root}/vendor/hybridauth/hybridauth/hybridauth/Hybrid/Providers`

Then, create a configuration file in `{project-root}/app/config` folder like

```php
return array(

    'base_url' => 'http://tamedbitches.app:8000/social/auth',

    'providers' => array (

        'Facebook' => array (
            'enabled' => TRUE,
            'keys'    => array ( 'id' => '81084046564????', 'secret' => 'fdd5d7f19d67bd220c855940da56????' ),
            "scope"   => "email",
        ),

        "Kakao" => array (
            "enabled" => TRUE,
            "keys"    => array ( "id" => "53a30c18096a18bda29162111208????", "secret" => "????" ),
        ),

        'Naver' => array (
            'enabled' => TRUE,
            'keys'    => array ( 'id' => 'ILH9AXW0mfxQZf_U????', 'secret' => '????' )
        ),
    ),

);
```

To register IoC binding, add the following snippet into `{project-root}/app/start/global.php`

```
App::bind('Hybrid_Auth', function() {
    return new Hybrid_Auth(app_path().'/config/hybridauth.php');
});
```

* I assumed you're using Laravel 4.x PHP framework. But, the hybridauth
package itself isn't necessarily dependent on any specific PHP frameworks.

Sample Outputs
--------------

1. 페이스북 로그인 후 사용자 정보 -- http://localhost.app:8000/social/facebook

```
object(Hybrid_User_Profile)[244]
  public 'identifier' => string '10152723746810141' (length=17)
  public 'webSiteURL' => string '' (length=0)
  public 'profileURL' => string 'https://www.facebook.com/app_scoped_user_id/10152723746810141/' (length=62)
  public 'photoURL' => string 'https://graph.facebook.com/10152723746810141/picture?width=150&height=150' (length=73)
  public 'displayName' => string 'Jinseok Oh' (length=10)
  public 'description' => string 'A daydreamer constantly seeking some everlasting value, inspiration, and a great fortune.' (length=89)
  public 'firstName' => string 'Jinseok' (length=7)
  public 'lastName' => string 'Oh' (length=2)
  public 'gender' => string 'male' (length=4)
  public 'language' => null
  public 'age' => null
  public 'birthDay' => int 17
  public 'birthMonth' => int 1
  public 'birthYear' => int 1970
  public 'email' => string 'jinseokoh@hotmail.com' (length=21)
  public 'emailVerified' => string 'jinseokoh@hotmail.com' (length=21)
  public 'phone' => null
  public 'address' => null
  public 'country' => null
  public 'region' => string '' (length=0)
  public 'city' => null
  public 'zip' => null
  public 'username' => string '' (length=0)
  public 'coverInfoURL' => string 'https://graph.facebook.com/10152723746810141?fields=cover' (length=57)
```

2. 카카오톡 로그인 후 사용자 정보 -- http://localhost.app:8000/social/kakao

```
object(Hybrid_User_Profile)[244]
  public 'identifier' => int 6559694
  public 'webSiteURL' => null
  public 'profileURL' => null
  public 'photoURL' => string 'http://mud-kage.kakao.co.kr/14/dn/btqbGIgs1q5/g3NMfKsrN1Hd1Pki7GotBk/o.jpg' (length=74)
  public 'displayName' => string '오진석' (length=9)
  public 'description' => null
  public 'firstName' => null
  public 'lastName' => null
  public 'gender' => null
  public 'language' => null
  public 'age' => null
  public 'birthDay' => null
  public 'birthMonth' => null
  public 'birthYear' => null
  public 'email' => null
  public 'emailVerified' => null
  public 'phone' => null
  public 'address' => null
  public 'country' => null
  public 'region' => null
  public 'city' => null
  public 'zip' => null
```

3. 네이버 로그인 후 사용자 정보 -- http://localhost.app:8000/social/naver

```
object(Hybrid_User_Profile)[244]
  public 'identifier' => string '18f767fbc55907ddcb476ec63c69014b43941799b9f8b019bb5dd570b7e7e871' (length=64)
  public 'webSiteURL' => null
  public 'profileURL' => null
  public 'photoURL' => string 'https://phinf.pstatic.net/contactthumb.phinf/profile/blog/82/44/chuckau.jpg?type=s80' (length=84)
  public 'displayName' => string '어쨌거나' (length=12)
  public 'description' => null
  public 'firstName' => null
  public 'lastName' => null
  public 'gender' => string 'male' (length=4)
  public 'language' => null
  public 'age' => string '40-49' (length=5)
  public 'birthDay' => string '17' (length=2)
  public 'birthMonth' => string '01' (length=2)
  public 'birthYear' => null
  public 'email' => string 'chuckau@naver.com' (length=17)
  public 'emailVerified' => string 'chuckau@naver.com' (length=17)
  public 'phone' => null
  public 'address' => null
  public 'country' => null
  public 'region' => null
  public 'city' => null
  public 'zip' => null
```

Buy me a beer if you use my code
--------------------------------

If you’re also interested in practicing nerdism in Seoul area, perhaps we can get together
and have a chance to know each other better or just for the sake of munching dried squid. :beer: Happy coding!

References
----------

hybridauth 패키지 (http://hybridauth.sourceforge.net/)

카카오 계정으로 로그인 (https://developers.kakao.com/docs/restapi) 

네이버 아이디로 로그인 (http://developer.naver.com/wiki/pages/NaverLogin)

Contact me
----------

Chuck JS. Oh

http://facebook.com/chuckoh

<jinseokoh@hotmail.com>
