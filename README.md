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
