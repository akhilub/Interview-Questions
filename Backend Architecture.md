Controller
	validate()
	hashPassword()
	saveUser()
	sendEmail()

1 . **MVC (Model-View-Controller)**
- Good for small apps
- Controller handles requests, Model Manages application data, View handles UI

Client -> Controller -> Model -> Database

2 . **MCS (Model-Controller-Service)**
- Used when the app grows
- Buisness logic moves to a Service Layer, so controllers stay clean and focused on HTTP Request

Client -> Controller -> **Service** -> Model -> Database

3 . **MCRS (Model-Controller-Repository-Service)**
- Used in larger systems
- A Repository layer handles database queries, keeping services focused on buisness logic.
- The idea is simple: separate responsibilities, so your code stays clean as the system grows

Client -> Controller -> Service -> **Repository** -> Database