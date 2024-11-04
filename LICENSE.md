public class Main {


    public static void main(String[] args) {

        Runnable printA = new PrintChar('a', 30);
        Runnable printB = new PrintChar('b', 20);
        Runnable print100 = new PrintNum(40);

        Thread thread1 = new Thread(printA);
        Thread thread2 = new Thread(printB);
        Thread thread3 = new Thread(print100);

        // Start threads
        Thread thread4 = new Thread(new PrintChar('c' , 25));

        thread4.setPriority(7);
        thread4.start();
        thread1.start();
        thread2.start();
        thread3.start();


    }
}

class PrintChar implements Runnable {

    private char charToPrint;
    private int times;

    public PrintChar(char c, int t) {
        charToPrint = c;
        times = t;
    }

    public void run() {
        for (int i = 0; i < times; i++) {
            System.out.print(charToPrint);
        }
    }
   // public void run(){}
}

class PrintNum implements Runnable {
    private int lastNum;

    public PrintNum(int n) {
        lastNum = n;
    }

    @Override
    public void run() {
        for (int i = 1; i <= lastNum; i++) {
            System.out.print(" " + i);
        }
    }
}
