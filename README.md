# an-jwt-auth
## Аутентификация JWT для WP REST API

Расширяет API-интерфейс WP REST, используя аутентификацию веб-токенов JSON в качестве метода аутентификации.

JSON Web Token (JWT) — это открытый стандарт ([RFC 7519](https://tools.ietf.org/html/rfc7519)) для создания токенов доступа, основанный на формате JSON. Как правило, используется для передачи данных для аутентификации в клиент-серверных приложениях. Токены создаются сервером, подписываются секретным ключом и передаются клиенту, который в дальнейшем использует данный токен для подтверждения своей личности.

### ТРЕБОВАНИЯ

#### WP REST API V2

Этот плагин был задуман для расширения возможностей плагина WP REST API V2 и, конечно, был построен на его основе.

Итак, чтобы использовать wp-api-jwt-auth, вам нужно установить и активировать WP REST API .

### ВКЛЮЧИТЬ HTTP ЗАГОЛОВОК АВТОРИЗАЦИИ

На большинстве хостингов по умолчанию заголовок **авторизации HTTP** отключен .

Чтобы включить эту опцию, вам нужно отредактировать ваш файл **.htaccess**, добавив следующее

`
RewriteEngine on
RewriteCond %{HTTP:Authorization} ^(.*)
RewriteRule ^(.*) - [E=HTTP_AUTHORIZATION:%1]
`

#### WPENGINE

Чтобы включить эту опцию, вам нужно отредактировать ваш файл **.htaccess**, добавив следующее

См. Https://github.com/Tmeister/wp-api-jwt-auth/issues/1.

`
SetEnvIf Authorization "(.*)" HTTP_AUTHORIZATION=$1
`

#### НАСТРОЙКА ПОДДЕРЖКИ CORS

Плагин имеет возможность активировать Корс поддержку.

Чтобы включить поддержку CORs, отредактируйте файл wp-config.php и добавьте новую константу с именем **JWT_AUTH_CORS_ENABLE**

`
define('JWT_AUTH_CORS_ENABLE', true);
`

