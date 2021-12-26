import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        BattleField battleField = new BattleField();
        BattleField battleField2 = new BattleField();
        battleField.createBattleField();
        battleField2.createBattleField();
        System.out.println("Player 1, place your ships on the game field");
        battleField.printBattleField();
        BattleShips ships = new BattleShips();
        for (Ships ships1 : Ships.values()) {
            battleField.placeShip(ships, ships1.getName(), ships1.getCells());
        }
        System.out.println("Press Enter and pass the move to another player");
        try{
            System.in.read();
        } catch(Exception e){

        }
        battleField2.printBattleField();
        for (Ships ships1 : Ships.values()) {
            battleField2.placeShip(ships, ships1.getName(), ships1.getCells());
        }
        while (battleField.checkTheField() && battleField2.checkTheField()) {
            System.out.println("Press Enter and pass the move to another player");
            try{
                System.in.read();
            } catch(Exception e){

            }
            battleField.printCopyOfBattleField();
            System.out.println("---------------------");
            battleField.printBattleField();
            System.out.println("Player 1, it's your turn:");
            battleField.shot(battleField2);
            System.out.println("Press Enter and pass the move to another player");
            try{
                System.in.read();
            } catch(Exception e){

            }
            battleField2.printCopyOfBattleField();
            System.out.println("---------------------");
            battleField2.printBattleField();
            System.out.println("Player 2, it's your turn:");
            battleField2.shot(battleField);
        }
        System.out.println("You sank the last ship. You won. Congratulations!");
    }
}
public class BattleField {

    Scanner scanner = new Scanner(System.in);

    String[][] battleField;
    String[][] copyOfBattleField;

    static int size = 11;

    public BattleField() {
        battleField = new String[size][size];
        copyOfBattleField = new String[size][size];
    }

    public void createBattleField() {
        int num = 49;
        int num2 = 49;
        int symbol = 65;
        int symbol2 = 65;
        for (int i = 0; i < battleField.length; i++) {
            for (int j = 0; j < battleField[i].length; j++) {
                battleField[i][j] = "~";
                copyOfBattleField[i][j] = "~";
                if (i < 1 && j > 0) {
                    battleField[i][j] = String.valueOf((char) num++);
                    copyOfBattleField[i][j] = String.valueOf((char) num2++);
                } else if (i > 0 && j < 1) {
                    battleField[i][j] = String.valueOf((char) symbol++);
                    copyOfBattleField[i][j] = String.valueOf((char) symbol2++);
                }
            }
        }
        battleField[0][0] = " ";
        copyOfBattleField[0][0] = " ";
        battleField[0][10] = "10";
        copyOfBattleField[0][10] = "10";
    }

    public String[][] getBattleField() {
        return battleField;
    }

    public void placeShip(BattleShips newShip) {
        String fS = newShip.getFistSymbol();
        int fN = newShip.getFirstNum();
        String sS = newShip.getSecondSymbol ();
        int sN = newShip.getSecondNum();
        if (fN == sN) {
            for (int i = getIntegers(fS); i <= getIntegers(sS); i++) {
                for (int j = fN; ; ) {
                    battleField[i][j] = "O";
                    break;
                }
            }
        } else if (fS.equals(sS)) {
            for (int i = getIntegers(fS); i <= getIntegers(fS); i++) {
                for (int j = fN; j <= sN; j++) {
                    battleField[i][j] = "O";
                }
            }
        }
    }

    public static int getIntegers(String str1) {
        return switch (str1) {
            case "A" -> 1;
            case "B" -> 2;
            case "C" -> 3;
            case "D" -> 4;
            case "E" -> 5;
            case "F" -> 6;
            case "G" -> 7;
            case "H" -> 8;
            case "I" -> 9;
            case "J" -> 10;
            default -> 0;
        };
    }

    public void printCopyOfBattleField() {
        for (String[] array : copyOfBattleField) {
            for (String elem : array) {
                System.out.print(elem + " ");
            }
            System.out.println();
        }
    }

    public void printBattleField() {
        for (String[] array : battleField) {
            for (String elem : array) {
                System.out.print(elem + " ");
            }
            System.out.println();
        }
    }

    public void createPrintShip(BattleShips newShip) {
        placeShip(newShip);
        printBattleField();
    }

    public boolean isPlaceFree(BattleShips newBattleship) {
        boolean isFree = true;
        int n1 = newBattleship.getFirstNum();
        int l1 = getIntegers(newBattleship.getFistSymbol());
        int n2 = newBattleship.getSecondNum();
        int l2 = getIntegers(newBattleship.getSecondSymbol());
        if (l1 < battleField.length - 1 && n1 < 10) {
            if (battleField[l1][n1 - 1].equals("O") || battleField[l1][n1 + 1].equals("O"))
                isFree = false;
            if (battleField[l1 - 1][n1 - 1].equals("O") || battleField[l1 - 1][n1].equals("O") || battleField[l1 - 1][n1 + 1].equals("O"))
                isFree = false;
            if (battleField[l1 + 1][n1 - 1].equals("O") || battleField[l1 + 1][n1].equals("O") || battleField[l1 + 1][n1 + 1].equals("O"))
                isFree = false;
        } else if (l1 == battleField.length - 1 && n1 < 10) {
            if (battleField[l1][n1 - 1].equals("O") || battleField[l1][n1 + 1].equals("O"))
                isFree = false;
            if (battleField[l1 - 1][n1 - 1].equals("O") || battleField[l1 - 1][n1].equals("O") || battleField[l1 - 1][n1 + 1].equals("O"))
                isFree = false;
        } else if (l1 == battleField.length - 1 && n1 == 10) {
            if (battleField[l1][n1 - 1].equals("O"))
                isFree = false;
            if (battleField[l1 - 1][n1 - 1].equals("O") || battleField[l1 - 1][n1].equals("O"))
                isFree = false;
        } else if (l1 < battleField.length - 1 && n1== 10) {
            if (battleField[l1][n1 - 1].equals("O"))
                isFree = false;
            if (battleField[l1 - 1][n1 - 1].equals("O") || battleField[l1 - 1][n1].equals("O"))
                isFree = false;
            if (battleField[l1 + 1][n1 - 1].equals("O") || battleField[l1 + 1][n1].equals("O"))
                isFree = false;
        }
        if (l2 < battleField.length - 1 && n2 < battleField.length - 1) {
            if (battleField[l2][n2 - 1].equals("O") || battleField[l2][n2 + 1].equals("O"))
                isFree = false;
            if (battleField[l2 - 1][n2 - 1].equals("O") || battleField[l2 - 1][n2].equals("O") || battleField[l2 - 1][n2 + 1].equals("O"))
                isFree = false;
            if (battleField[l2 + 1][n2 - 1].equals("O") || battleField[l2 + 1][n2].equals("O") || battleField[l2 + 1][n2 + 1].equals("O"))
                isFree = false;
        } else if (l2 == battleField.length - 1 && n2 < battleField.length - 1) {
            if (battleField[l2][n2 - 1].equals("O") || battleField[l2][n2 + 1].equals("O"))
                isFree = false;
            if (battleField[l2 - 1][n2 - 1].equals("O") || battleField[l2 - 1][n2].equals("O") || battleField[l2 - 1][n2 + 1].equals("O"))
                isFree = false;
        } else if (l2 < battleField.length - 1 && n2 == battleField.length - 1) {
            if (battleField[l2][n2 - 1].equals("O"))
                isFree = false;
            if (battleField[l2 - 1][n2 - 1].equals("O") || battleField[l2 - 1][n2].equals("O"))
                isFree = false;
            if (battleField[l2 + 1][n2 - 1].equals("O") || battleField[l2 + 1][n2].equals("O"))
                isFree = false;
        } else if (l2 == battleField.length - 1 && n2 == battleField.length - 1) {
            if (battleField[l2][n2 - 1].equals("O"))
                isFree = false;
            if (battleField[l2 - 1][n2 - 1].equals("O") || battleField[l2 - 1][n2].equals("O"))
                isFree = false;
        }
        return isFree;
    }

    public void placeShip(BattleShips ships, String name, int cells) {
        boolean isCreated = true;
        System.out.printf("Enter the coordinates of the %s (%d cells):\n", name, cells);
        while (isCreated) {
            String coord1 = scanner.nextLine();
            ships.coordinates(coord1);
             if (ships.getFirstNum() != ships.getSecondNum() && !ships.getFistSymbol().equals(ships.getSecondSymbol())) {
                 System.out.println("Error! Wrong ship location! Try again:");
             } else {
                 if (ships.getSecondNum() - ships.getFirstNum() == cells - 1
                        || BattleField.getIntegers(ships.getSecondSymbol()) - BattleField.getIntegers(ships.getFistSymbol()) == cells - 1) {
                     if (!isPlaceFree(ships)) {
                         System.out.println("Error! You placed it too close to another one. Try again:");
                     } else {
                         createPrintShip(ships);
                         isCreated = false;
                     }
                } else {
                    System.out.printf("Error! Wrong length of the %s! Try again:\n", name);
                }
            }
        }
    }

    public void shot(BattleField newBattlefield) {
        String[][] enemyBattleField = newBattlefield.getBattleField();
        String shot = scanner.next();
        String fl = shot.substring(0, 1);
        int l1 = getIntegers(fl);
        int n = Integer.parseInt(shot.substring(1));
        int n1 = n < battleField.length ?  n : 0;
        if (enemyBattleField[l1][n1].equals("O")) {
            enemyBattleField[l1][n1] = "X";
            copyOfBattleField[l1][n1] = "X";
            if (!checkTheField() || !newBattlefield.checkTheField()) {
                return;
            } else {
                if (isSank(l1, n1)) {
                    System.out.println("You sank a ship! Specify a new target:");
                } else {
                    System.out.println("You hit a ship!");
                }
            }
        } else if (enemyBattleField[l1][n1].equals("~")) {
            enemyBattleField[l1][n1] = "M";
            copyOfBattleField[l1][n1] = "M";
            System.out.println("You missed!");

        } else if (enemyBattleField[l1][n1].equals("X")) {
            System.out.println("You missed!");
        } else {
            System.out.println("Error! You entered the wrong coordinates! Try again:");
            shot(newBattlefield);
        }
    }

    public boolean isSank(int l1, int n1) {
        boolean isSank = true;
        if (l1 < battleField.length - 1 && n1 < 10) {
            if (battleField[l1][n1 - 1].equals("O") || battleField[l1][n1 + 1].equals("O"))
                isSank = false;
            if (battleField[l1 - 1][n1 - 1].equals("O") || battleField[l1 - 1][n1].equals("O") || battleField[l1 - 1][n1 + 1].equals("O"))
                isSank = false;
            if (battleField[l1 + 1][n1 - 1].equals("O") || battleField[l1 + 1][n1].equals("O") || battleField[l1 + 1][n1 + 1].equals("O"))
                isSank = false;
        } else if (l1 == battleField.length - 1 && n1 < 10) {
            if (battleField[l1][n1 - 1].equals("O") || battleField[l1][n1 + 1].equals("O"))
                isSank = false;
            if (battleField[l1 - 1][n1 - 1].equals("O") || battleField[l1 - 1][n1].equals("O") || battleField[l1 - 1][n1 + 1].equals("O"))
                isSank = false;
        } else if (l1 == battleField.length - 1 && n1 == 10) {
            if (battleField[l1][n1 - 1].equals("O"))
                isSank = false;
            if (battleField[l1 - 1][n1 - 1].equals("O") || battleField[l1 - 1][n1].equals("O"))
                isSank = false;
        } else if (l1 < battleField.length - 1 && n1== 10) {
            if (battleField[l1][n1 - 1].equals("O"))
                isSank = false;
            if (battleField[l1 - 1][n1 - 1].equals("O") || battleField[l1 - 1][n1].equals("O"))
                isSank = false;
            if (battleField[l1 + 1][n1 - 1].equals("O") || battleField[l1 + 1][n1].equals("O"))
                isSank = false;
        }
        return isSank;
    }

    public boolean checkTheField() {
        boolean isShipsLeft = false;
        for (String[] array : battleField) {
            for (String elem : array) {
                if (elem == "O")
                    isShipsLeft = true;
            }
        }
        return isShipsLeft;
    }
}
public class BattleShips {
    String[] ship;
    String fistSymbol;
    int firstNum;
    String secondSymbol;
    int secondNum;

    public void coordinates(String str1) {
        String[] str1Array = str1.split(" ");
        if (str1Array[0].substring(0, 1).compareTo(str1Array[1].substring(0, 1)) < 0) {
            this.fistSymbol = str1Array[0].substring(0, 1);
            this.firstNum = Math.min(Integer.parseInt(str1Array[0].substring(1)), Integer.parseInt(str1Array[1].substring(1)));
            this.secondSymbol = str1Array[1].substring(0, 1);
            this.secondNum = Math.max(Integer.parseInt(str1Array[0].substring(1)), Integer.parseInt(str1Array[1].substring(1)));
        } else {
            this.fistSymbol = str1Array[1].substring(0, 1);;
            this.firstNum = Math.min(Integer.parseInt(str1Array[0].substring(1)), Integer.parseInt(str1Array[1].substring(1)));
            this.secondSymbol = str1Array[0].substring(0, 1);
            this.secondNum = Math.max(Integer.parseInt(str1Array[0].substring(1)), Integer.parseInt(str1Array[1].substring(1)));
        }
    }

    public String getFistSymbol() {
        return this.fistSymbol;
    }

    public int getFirstNum() {
        return this.firstNum;
    }

    public String getSecondSymbol() {
        return this.secondSymbol;
    }

    public int getSecondNum() {
        return this.secondNum;
    }
}
public enum Ships {
    AIRCRAFT_CARRIER("Aircraft Carrier", 5),
    BATTLESHIP("Battleship", 4),
    SUBMARINE("Submarine", 3),
    CRUISER("Cruiser", 3),
    DESTROYER("Destroyer", 2);

    String name;
    int cells;

    Ships(String name, int cells) {
        this.name = name;
        this.cells = cells;
    }

    public String getName() {
        return this.name;
    }

    public int getCells() {
        return this.cells;
    }
}
