# @Controller

Spring에서 컨트롤러를 지정해주기 위한 어노테이션은 @Controller와 @RestController가 있다.
@RestController(Restuful 웹서비스의 컨트롤러)와는 HTTP Response Body가 생성되는 방식이 다르다.



![[Pasted image 20231105150254.png]]


전통적인 spring MVC 컨트롤러 : @Controller -> view 반환하기 위해 사용

1. Client는 URI 형식으로 웹 서비스에 요청을 보낸다.
2. DispatcherServlet이 요청을 처리할 대상을 찾는다.
3. HandlerAdapter을 통해 요청을 Controller로 위임한다.
4. Controller는 요청을 처리한 후에 ViewName을 반환한다.
5. DispatcherServlet은 ViewResolver를 통해 ViewName에 해당하는 View를 찾아 사용자에게 반환한다.

View를 렌더링하기 위해서는 ViewResolver가 사용된다.

> Controller로 Data 반환하기 : @ResponseBody


```java
@Controller
@RequiredArgsConstructor
public class UserController {

	private final UserService userService;

	@GetMapping(value = "/users")
	public @ResponseBody ResponseEntity<User> findUser(@RequestParam("userName") String userName) {
		return ResponseEntity.ok(userService.findUser(user));
	}

	@GetMapping(value = "/users/detailView")
	public String detailView(Model model, @RequestParam("userName") String userName) {
		User user = userService.findUser(userName);
		model.addAttribute("user", user);
		return "/users/detailView";
	}
}
```


# @RestController
: @Controller에 @ResponseBody가 추가된 것
Json 형태로 객체 데이터를 반환하는 것

데이터를 응답으로 제공하는 REST API를 개발할 때 주로 사용하며 객체를 ResponseEntity로 감싸서 반환.

동작과정은 @Controller와 동일.

```java
@RestControlle
@RequiredArgsConstructor
public class UserController {

	private final UserService userService;
	
	@GetMapping(value = "/users")
	public User findUser(@RequestParam("userName") String userName) {
		return userService.findUser(user);
	}
	
	@GetMapping(value = "/users")
	public ResponseEntity<User> findUserWithResponseEntity(@RequestParam("userName") String userName) {
		return ResponseEntity.ok(userService.findUser(user)); 
	}
}
```

