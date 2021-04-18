# API YaMDb
<h2>База отзывов о фильмах, книгах и музыке.</h2>

  Проект YaMDb собирает отзывы (Review) пользователей на произведения (Title). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) может быть расширен (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).

<h2>Техническое описание проекта YaMDb</h2>

  К проекту по адресу <b>/redoc</b> подключена документация API YaMDb. В ней описаны шаблоны запросов к API и структура ожидаемых ответов. Для каждого запроса указаны уровни прав доступа: пользовательские роли, которым разрешён запрос.

<h2>Пользовательские роли</h2>

<b>Аноним</b> — может просматривать описания произведений, читать отзывы и комментарии.

<b>Аутентифицированный пользователь</b> (user)— может читать всё, как и Аноним, дополнительно может публиковать отзывы и ставить рейтинг произведениям (фильмам/книгам/песенкам), может комментировать чужие отзывы и ставить им оценки; может редактировать и удалять свои отзывы и комментарии.

<b>Модератор</b> (moderator) — те же права, что и у Аутентифицированного пользователя плюс право удалять и редактировать любые отзывы и комментарии.

<b>Администратор</b> (admin) — полные права на управление проектом и всем его содержимым. Может создавать и удалять произведения, категории и жанры. Может назначать роли пользователям.

<h2>Алгоритм регистрации пользователей</h2>

1. Пользователь отправляет POST-запрос с параметром email на /api/v1/auth/email/.
2. YaMDB отправляет письмо с кодом подтверждения (confirmation_code) на адрес email.
3. Пользователь отправляет POST-запрос с параметрами email и confirmation_code на /api/v1/auth/token/, в ответе на запрос ему приходит token (JWT-токен).

<h2>Ресурсы API YaMDb</h2>

Ресурс <b>AUTH</b>: аутентификация.

Ресурс <b>USERS</b>: пользователи.

Ресурс <b>TITLES</b>: произведения, к которым пишут отзывы (определённый фильм, книга или песенка).

Ресурс <b>CATEGORIES</b>: категории (типы) произведений («Фильмы», «Книги», «Музыка»).

Ресурс <b>GENRES</b>: жанры произведений. Одно произведение может быть привязано к нескольким жанрам.

Ресурс <b>REVIEWS</b>: отзывы на произведения. Отзыв привязан к определённому произведению.

Ресурс <b>COMMENTS</b>: комментарии к отзывам. Комментарий привязан к определённому отзыву.