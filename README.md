-import java.util.concurrent.Semaphore;

class TrafficControlSystem {
    Semaphore semaphore = new Semaphore(1); // Single lane semaphore

    void carArrived() {
        try {
            semaphore.acquire(); // Acquiring the semaphore
            System.out.println("Car arrived at the intersection.");
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }

    void carDeparted() {
        System.out.println("Car departed from the intersection.");
        semaphore.release(); // Releasing the semaphore
    }
}

class Car implements Runnable {
    TrafficControlSystem trafficControlSystem;

    public Car(TrafficControlSystem trafficControlSystem) {
        this.trafficControlSystem = trafficControlSystem;
    }

    @Override
    public void run() {
        trafficControlSystem.carArrived();
        // Simulating some work
        try {
            Thread.sleep(2000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        trafficControlSystem.carDeparted();
    }
}

public class Main {
    public static void main(String[] args) {
        TrafficControlSystem trafficControlSystem = new TrafficControlSystem();

        // Creating and starting multiple threads representing cars
        for (int i = 1; i <= 5; i++) {
            Thread carThread = new Thread(new Car(trafficControlSystem), "Car-" + i);
            carThread.start();
        }
    }
}
 👋 Hi, I’m @2025SHIVAM
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
2025SHIVAM/2025SHIVAM is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
