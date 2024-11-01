# J6

## 1. The program is not consistent. 

## 2. The order will still print out randomly but there will be one second between each print so it won't be clustered.

## 3. The main method adds a 3rd thread, and the other two threads run separately from main.

## 4. "Good Morning" will be printed out 5 times when morning thread is running, then the morning and afternoon thread start alternating, afternoon thread will finish 5 seconds later then morning and the last print will be "Good Afternoon". 

## 5. join() makes the current thread wait around 0 seconds while join(10) makes the current thread wait for a maximum of 10 seconds. 

## 6. isAlive() is used to see the status of the thread and is returned as a boolean without waiting for the thread to terminate, while join() is when the current thread will wait for the referenced thread to terminate.

## 7. Because there are more than one thread running at one time, the output varies. It will stay consistent in printing out each animal based on their speed. It print out in this format: "animal" "lap" "lap number" and will hae have statments such as "On your marks, get set, go!" and "Cheetah Finished!". 

## 8. Letting the Hare start earlier gives it more time to run the race and finish first: 
$ javac *.java
$ java AnimalFootRace
/* AnimalFootRace.java */
public class AnimalFootRace {
    public static void main(String[] args) {
        Thread tortoiseThread = new AnimalRacerThread("Tortoise", 5);
        Thread hareThread = new AnimalRacerThread("Hare", 100);
        Thread cheetahThread = new AnimalRacerThread("Cheetah", 50);

        System.out.println("On your marks, get set, go!");
        hareThread.start();
        try{
            System.out.println("Joining the morning thread for 5 seconds...");
            hareThread.join(500);
            } cath(InterruptedException e){
                System.out.println("Interrupted while joining a thread...");
            }
            tortoiseThread.start();
        cheetahThread.start();
    }
}
/* AnimalRacerThread.java */
public class AnimalRacerThread extends Thread {
    public static final int NUM_LAPS = 8;
    private String animalName;
    private int animalSpeed;

    public AnimalRacerThread(String animalName, int animalSpeed) {
        this.animalName = animalName;
        this.animalSpeed = animalSpeed;
    }

    @Override
    public void run() {
        for (int i = 1; i <= NUM_LAPS; i++) {
            System.out.println(animalName + " lap " + i);
            try {
                Thread.sleep(1000 / animalSpeed);
            } catch (InterruptedException e) {
                System.out.println("Interrupted while sleeping...");
            }
        }
        System.out.println(animalName + "Finished!");
    }
}

## 9. Adding the animal dog with a 10 second head start allows for the cheeatah to finish first, then the Hare, then the dog, and lastly the Tortoise.
$ javac *.java
$ java AnimalFootRace
/* AnimalFootRace.java */
public class AnimalFootRace {
    public static void main(String[] args) {
        Thread tortoiseThread = new AnimalRacerThread("Tortoise", 5);
        Thread hareThread = new AnimalRacerThread("Hare", 20);
        Thread cheetahThread = new AnimalRacerThread("Cheetah", 50);
        Thread jaguarThread = new AnimalRacerThread("Dog," 10);

        System.out.println("On your marks, get set, go!");
        tortoiseThread.start();
        hareThread.start();
        cheetahThread.start();
        jaguarThread.start();
    }
}
/* AnimalRacerThread.java */
public class AnimalRacerThread extends Thread {
    public static final int NUM_LAPS = 8;
    private String animalName;
    private int animalSpeed;

    public AnimalRacerThread(String animalName, int animalSpeed) {
        this.animalName = animalName;
        this.animalSpeed = animalSpeed;
    }

    @Override
    public void run() {
        for (int i = 1; i <= NUM_LAPS; i++) {
            System.out.println(animalName + " lap " + i);
            try {
                Thread.sleep(1000 / animalSpeed);
            } catch (InterruptedException e) {
                System.out.println("Interrupted while sleeping...");
            }
        }
        System.out.println(animalName + "Finished!");
    }
}

## 10. It is possible to create more than one instances of the Singleton class but it is not always possible. 

## 11. It is not possible to create more than one instance of the Singelton class if 2 thread attempt to call the getInstance() method at the same time. 

## 12. The code prints from 1 to 2000 and "Status flag changed to true in simple thread one." in a loop. It keeps on looping because it is not getting the statudflag update, meaning it keeps on running.

## 13. The code now stops looping because it is getting the updates. 

## 14. If it calls at the sme time, the updates could be inconsistent. To fix this you can add  the synchronized keyword to the makeBid().
