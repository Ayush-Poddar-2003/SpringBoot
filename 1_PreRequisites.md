# DESIGN PATTERN ?

TIGHT & LOOSE COUPLING ?  
Tells how two classes are dependant over each other.  
Tight -> More Dependant  
Loose -> Less Dependant

For eg:-

```java
//NotificationService.java
public class NotificationService {
    public void send(String message){
        System.out.println("From notification service : " + message);
    }
}

//UserService.java
public class UserService {
    NotificationService nn = new NotificationService();

    public void notifyUser(String message){
        nn.send(message);
    }
}

//AppMain.java
public class AppMain {
    public static void main(String[] args) 
    {
        UserService uu = new UserService();
        uu.notifyUser("Order placed");
    }
}
```
If you do slight changes in parent ie NotificationService class, you gotta have to change everywhere.

---
### LOOSE COUPLING -
To implement loose coupling we have to use `interfaces`   
Making NotificationService as parent and interface, and implemting it   

```java
//NotificaionService.java : Interface as a base
public interface NotificationService {
    void send(String message);
}


//EmailNotificationService.java
public class EmailNotificationService implements NotificationService 
{
    @Override //ReDefining interface method
    public void send(String message) {
        System.out.println("Email " + message);
    }
}


//UserService.java
public class UserService {
    NotificationService nn;

    //constructor
    public UserService(NotificationService nn) {
        this.nn = nn;
    }
    public void notifyUser(String message){
        nn.send(message);
    }
}

//AppMain.java
public class AppMain {
    public static void main(String[] args) 
    {
        NotificationServices ne = new EmailNotificationService();
        
        NotificationServices ns = new SMSNotificationService();
        
        UserService uu = new UserService();
        uu.notifyUser("Order Placed")
    }
}
```
Simalry we can use it with any notification be it sms, call, push or any