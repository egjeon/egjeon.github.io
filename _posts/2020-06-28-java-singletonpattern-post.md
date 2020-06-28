---
title: "[Java]디자인패턴-Singleton pattern"
date: 2020-06-28 18:44:00 
categories: Java DesignPattern
---



# Singleton Pattern에 대하여
#### 현업에서, 협업 유틸등을 만들거나, 할때에 유용하게 쓰인다. 
#### 단 하나만 존재하는 인스턴스를 사용하는 패턴을 우리는,  -Singleton pattern 이라고 부른다.

생성자는 private 으로, static으로 유일한 객체를 생성 해준다.<br>
외부에서 유일한 객체를 참조할 수 있는 public static get() 메서드를 구현 해준다.<br>

new 연산자를 이용하여 여러 객체가 생성될 때에 문제가 될 수 있는 객체를 Singleton Pattern으로 방지 해 줄 수 있다.<br>
100번 불러도 똑같은 주소를 참조한다.<br>
싱글톤 패턴 유틸로는, 날짜는 하나의 값을 참조하여야 하기 때문에, Calendar클래스를 생각 할 수 있다.<br>
Calendar호출시 , new 하여 메모리에 직접적으로 인스턴스를 생성하지 않고, Calendar calendar = Calendar.getInstance();를 호출 하여 사용 하듯이,<br>
우리도 필요한 유틸을 만들때에, 이러한 패턴으로 만듬으로써, 몇번을 호출 하여도, 변하지 않는 값을 확인 할 수 있다.<br>

## 싱글톤 패턴 예제
    
    Class Company를 만든다고 가정하자
    
    public Class Company{
    
        private static Company instance = new Company(); // 인스턴스를 static으로 생성 해줌.
    
        private Company(){} // default 생성자가 불리지 않게 은닉시켜주어 선언해준다.
    
        public static Company getInstance(){ // getInstance의 이름을 가진 메서드를 정의 해준다.
            if(instance == null)
                insatnce = new Company(); // NULL일 경우가 없지만 체크하여 생성자가 new로 메모리에 올라가지 않은상태로 호출 당할 시에 ,  한번 더 메모리에 올리는 작업을 한다.
            return instance; //반환.
        }
    }
#### 위의 예제만 보아도 확실히 알 수 있듯이, private 생성자를 만들어 둠으로써, 외부에서 인스턴스 생성이 불가능하게 함을 알 수 있다.



