---
title: HandlerMethodArgumentResolver 인터페이스를 이용한 Controller 커스텀 파라미터 객체 만들기
catalog: true
date: 2019-01-28
subtitle: HandlerMethodArgumentResolver
header-img:
tags:
- Java
- Spring



---

# HandlerMethodArgumentResolver 인터페이스를 이용한 Controller 커스텀 파라미터 객체 만들기
이 인스터페이스는 전략 패턴의 일종으로 컨트롤러 메서드에서 특정 조건에 해당하는 파라미터에 바인딩 해주는 전략 인터페이스이다. 따라서 AOP로 모든 메서드를 일일이 찾아서 데이터를 바인딩 할 필요없이 어노테이션을 만들어 쉽게 바인딩 할 수 있다.

예를 들어 컨트롤러에서 세션을 조회해야 하거나 HttpServletRequest에서 토큰 또는 쿠키 정보를 기반으로 인증 객체를 만들어야 한다고 가정해보자. 그렇게 되면 이러한 객체를 만들기 위해서는 아래의 소스같이 session에서 유저정보를 가져오거나 request 정보에서 인증정보를 가져오는 중복 코드가 발생할 수 있다. 이러한 문제를 HandlerMethodArgumentResolver를 이용하면 쉽게 해결할 수 있다.
