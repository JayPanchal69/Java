```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class RandomMessagePassing {

    public static void main(String[] args) {
        int numberOfCommandos = 10;

        // Create a list to represent the commandos
        List<Integer> commandoOrder = new ArrayList<>();
        for (int i = 1; i <= numberOfCommandos; i++) {
            commandoOrder.add(i);
        }

        // Shuffle the order randomly
        Collections.shuffle(commandoOrder);

        // Find the position of Band #1 and Band #10
        int indexOfBand1 = commandoOrder.indexOf(1);
        int indexOfBand10 = commandoOrder.indexOf(10);

        // Ensure Band #1 is at the beginning and Band #10 is at the end
        Collections.swap(commandoOrder, 0, indexOfBand1);
        Collections.swap(commandoOrder, numberOfCommandos - 1, indexOfBand10);

        // Simulate passing the message
        for (int i = 0; i < numberOfCommandos - 1; i++) {
            System.out.println("Band #" + commandoOrder.get(i) + " passes the message to Band #" + commandoOrder.get(i + 1));
        }

        System.out.println("Band #10 has received the message.");
    }
}

```



```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class RandomMessagePassing {

    public static void main(String[] args) {
        int numberOfCommandos = 10;

        // Create a list to represent the commandos
        List<Integer> commandoOrder = new ArrayList<>();
        for (int i = 1; i <= numberOfCommandos; i++) {
            commandoOrder.add(i);
        }

        // Shuffle the order randomly
        Collections.shuffle(commandoOrder);

        // Find the position of Band #1 and Band #10
        int indexOfBand1 = commandoOrder.indexOf(1);
        int indexOfBand10 = commandoOrder.indexOf(10);

        // Ensure Band #1 is at the beginning and Band #10 is at the end
        Collections.swap(commandoOrder, 0, indexOfBand1);
        Collections.swap(commandoOrder, numberOfCommandos - 1, indexOfBand10);

        // Simulate passing the message
        for (int i = 0; i < numberOfCommandos - 1; i++) {
            System.out.println("Band #" + commandoOrder.get(i) + " passes the message to Band #" + commandoOrder.get(i + 1));
        }

        System.out.println("Band #10 has received the message.");
    }
}

```




```java
import java.util.Random;

class Soldier {
    private final int id;
    private double position;

    public Soldier(int id, double position) {
        this.id = id;
        this.position = position;
    }

    public int getId() {
        return id;
    }

    public double getPosition() {
        return position;
    }

    public void setPosition(double position) {
        this.position = position;
    }
}

public class CircularFieldCommunication {
    private static final int NUM_SOLDIERS = 8;
    private static final double FIELD_RADIUS = 100.0; // Assume a circular field with a radius of 100 meters
    private static final double MIN_DISTANCE = 10.0; // Minimum distance required for passing information

    public static void main(String[] args) {
        Soldier[] soldiers = new Soldier[NUM_SOLDIERS];

        // Initialize soldiers with random positions in the field
        Random random = new Random();
        for (int i = 0; i < NUM_SOLDIERS; i++) {
            double position = random.nextDouble() * 2 * Math.PI; // Random angle in radians
            soldiers[i] = new Soldier(i + 1, position);
        }

        // Simulate soldier movements and information passing until Soldier 7 receives the information
        int time = 0;
        boolean informationPassed = false;
        while (!informationPassed) {
            moveSoldiers(soldiers);
            informationPassed = passInformation(soldiers);
            System.out.println("Soldier positions at time " + time + " seconds:");
            for (Soldier soldier : soldiers) {
                System.out.println("Soldier " + soldier.getId() + ": " + soldier.getPosition());
            }
            System.out.println();
            time += 20;
        }

        System.out.println("Information passed to Soldier 7 at time " + (time - 20) + " seconds.");
    }

    private static void moveSoldiers(Soldier[] soldiers) {
        Random random = new Random();
        for (Soldier soldier : soldiers) {
            double displacement = random.nextDouble() * 2 * Math.PI; // Random angle increment in radians
            double newPosition = soldier.getPosition() + displacement;
            soldier.setPosition(newPosition);
        }
    }

    private static boolean passInformation(Soldier[] soldiers) {
        Soldier sender = soldiers[0]; // Soldier 1 is the sender
        Soldier receiver = soldiers[6]; // Soldier 7 is the receiver

        double distance = calculateDistance(sender.getPosition(), receiver.getPosition());
        if (distance <= MIN_DISTANCE) {
            return true; // Information passed to Soldier 7
        }

        for (int i = 1; i < NUM_SOLDIERS; i++) {
            Soldier currentSoldier = soldiers[i];
            distance = calculateDistance(currentSoldier.getPosition(), receiver.getPosition());
            if (distance <= MIN_DISTANCE) {
                System.out.println("Soldier " + currentSoldier.getId() + " passes information to Soldier " + receiver.getId());
                return false; // Information passed to another soldier, but not yet to Soldier 7
            }
        }

        return false; // Information not yet passed to Soldier 7
    }

    private static double calculateDistance(double angle1, double angle2) {
        double angularDifference = Math.abs(angle1 - angle2);
        double distance = FIELD_RADIUS * angularDifference;
        if (distance > FIELD_RADIUS) {
            distance = 2 * Math.PI * FIELD_RADIUS - distance;
        }
        return distance;
    }
}

```

