# :newspaper: JPA
Java는 객체지향 언어이고, DataBase는 데이터 중심으로 구성되어 있다.  
이 패러다임의 불일치를 해결하기 위해 JPA를 사용한다. JPA는 ORM:Object-Relational-Mapping 이다.    
객체는 필드와 메소드를 가지고있고, 상속이 가능하다. 예를들어 팀 객체가 있고 필드로 회원 객체를 가지고있다고 하면, DB 테이블에 그대로 저장하는 것은 불가능 하다.   
팀을 저장하는 SQL을 작성하고 추가로 회원을 팀 안에 저장하는 SQL을 작성해야하는 번거로움이 있다.:-1:   
하지만 JPA는 이 같은 지루하고 반복적인 코드를 줄여주며, 개발자가 비즈니스 로직에 집중할 수 있도록 만들어준다!!:+1: 

# :hammer: PROJECT STACK
    Spring boot 2.4.2 / Spring Data JPA / Gradle / Lombok / h2 DataBase

# :pushpin:
- [JPA 구동 원리](/issues/jpa/JPA_구동원리.md)
- [JPA 영속성 개념](/issues/jpa/JPA_영속성개념.md)
