```
public abstract class Subject {

	private List<Observer> observers = new ArrayList<>();
	
	abstract void setState(String state);
	abstract String getState();
	
	public void attach(Observer observer) {
		observers.add(observer);
	}

	public void detach(Observer observer) {
		observers.remove(observer);
	}
	
	public void notifyObservers() {
		for (Observer observer : observers) {
			observer.update();
		}
	}
}
```

```
public class MessageStream extends Subject {

	private Deque<String> messageHistory = new ArrayDeque<>();
	
	@Override
	void setState(String message) {
		messageHistory.add(message);
		this.notifyObservers();
	}

	@Override
	String getState() {
		return messageHistory.getLast();
	}
}
```

```
public abstract class Observer {
	protected Subject subject;
	abstract void update();
}
```

```
public class PhoneClient extends Observer {

	public PhoneClient (Subject subject) {
		this.subject = subject;
		subject.attach(this);
	}
	
	public void addMessage(String message) {
		subject.setState(message + " - sent from phone");
	}
	
	@Override
	void update() {
		System.out.println("Phone Stream: " + subject.getState());
	}
}
```

```
public class TabletClient extends Observer {

	public TabletClient (Subject subject) {
		this.subject = subject;
		subject.attach(this);
	}
	
	public void addMessage(String message) {
		subject.setState(message + " - sent from tablet");
	}
	
	@Override
	void update() {
		System.out.println("Tablet Stream: " + subject.getState());
	}

}
```

```
public static void main(String args[]) {
	Subject subject = new MessageStream();
		
	PhoneClient phoneClient = new PhoneClient(subject);
	TabletClient tabletClient = new TabletClient(subject);
		
	phoneClient.addMessage("Here is a new message!");
	tabletClient.addMessage("Another new message!");
}
```
