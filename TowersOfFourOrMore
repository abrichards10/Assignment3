import java.util.*;

public class TowersOfFourOrMore {

    int[][] Board;
    int rows;
    int columns;
    int filled;

    public TowersOfFourOrMore(int balls_in_tube, int number_of_tubes, int fill){//constructor to initialise the data
        Board = new int[balls_in_tube][number_of_tubes];
        rows = balls_in_tube; //set rows to balls in tubes
        columns = number_of_tubes; //set columns to the number of tubes
        filled = fill;
    }

    // solve function
    public void solve_tower(){
        int oneCount = 0;
        int zeroCount = 0;
        int check_game_progress = 0;
        int total_count = 0;
        System.out.println("Sequence of moves:");

        // loop until all columns are filled with either one or zero
        while(total_count < filled - 1){
            int z = total_count + 2;
            // loop from the total_count to the total_count + 2
            for(int i = total_count; i < z; i++){
                // loop through the rows
                for(int j = 0; j < rows; j++){
                    // m stores the board at one less than rows - j (where the loop is now)
                    // and at one less than the columns minus wherever the game is
                    int m = Board[rows - j - 1][columns - check_game_progress - 1];
                    // add to the number of zeroes if board is at 0
                    if (Board[j][i] == 0)
                        zeroCount++;
                    // add to the number of ones if the board is at one
                    else if (Board[j][i] == 1)
                        oneCount++;
                    // set what we now have to the current board positions
                    Board[rows - j - 1][columns - check_game_progress - 1] = Board[j][i];
                    // print the board then set the positions to m
                    System.out.println(" t" + i + " - t" + (columns - check_game_progress - 1));
                    Board[j][i] = m;
                }
                // add to the progress check
                check_game_progress++;
            }

            // BREAK

            // reset the game check
            check_game_progress = 0;
            // set the index to the total_count
            int index = total_count;

            // if there are more zeroes than ones
            if (zeroCount >= oneCount) {
                int x = 0;
                int y = 0;

                // starting at columns -2, loop through columns
                for (int k = columns - 2; k < columns; k++) {
                    // loop through rows
                    for (int l = 0; l < rows; l++) {
                        // if the columns don't match and the board at the current index is zero
                        if (!checkCol(index)) {
                            if (Board[l][k] == 0) {
                                // basically use the same columns logic
                                // except increment x by one and set the current values to -1
                                Board[rows - x - 1][index] = Board[l][k];
                                System.out.println(" t" + k + " - t" + (index));
                                x++;
                                Board[l][k] = -1;
                            }
                            else {
                                // same as above
                                Board[rows - y - 1][index + 1] = Board[l][k];
                                System.out.println(" t" + k + " - t" + (index + 1));
                                y++;
                                Board[l][k] = -1;
                            }
                        }
                        else {
                            // if the column does match then we change the second value of one more than the index
                            // to our current values
                            Board[rows - y - 1][index + 1] = Board[l][k];
                            System.out.println(" t" + k + " - t" + (index + 1));
                            y++;
                            Board[l][k] = -1;
                        }
                    }
                }
            }

            // if the number of ones is greater
            else if (zeroCount < oneCount) {

                int x = 0;
                int y = 0;
                // loop through the columns and rows
                for (int k = columns - 2; k < columns; k++) {
                    for (int l = 0; l < rows; l++) {
                        // if the columns don't match and the board is equal to one
                        if (!checkCol(index)) {
                            if (Board[l][k] == 1) {
                                // Use the same logic
                                // change the index to our current values
                                // and increment x
                                Board[rows - x - 1][index] = Board[l][k];
                                System.out.println(" t" + k + " - t" + (index));
                                x++;
                                Board[l][k] = -1;
                            }
                            else {
                                Board[rows - y - 1][index + 1] = Board[l][k];
                                System.out.println(" t"+k+" - t"+(index+1));
                                y++;//increment y
                                Board[l][k] = -1;
                            }
                        }
                        else { // if the colums are equal we do the same thing and increment y this time
                            Board[rows - y - 1][index + 1] = Board[l][k];
                            System.out.println(" t" + k + " - t" + (index + 1));
                            y++;
                            Board[l][k] = -1;
                        }
                    }
                }
            }
            // we then reset the zeroes and ones and add to the count
            total_count++;
            zeroCount = 0;
            oneCount = 0;
        }
        System.out.println();
    }

    // check if the column is matching and not equal to -1
    public boolean checkCol(int column){
        // create a temp for the board ignoring the rows and looking at the columns
        int tempVal = Board[0][column];
        // create a flag to store a boolean
        boolean flag = true;
        // loop through the rows
        // if the board at the column is equal to the value at the temp
        // and the temp value is not -1, continue
        for(int i = 0;i < rows; i++){
            if(Board[i][column]==tempVal && tempVal!=-1){
                continue;
            }
            // otherwise, it's -1 and we return a false value
            else{
                flag = false;
                break;
            }
        }
        return flag;
    }

    // generate random order of ones and zeroes
    public void fill(){
        // loop through the array
        for(int i = 0; i < rows; i++){
            for(int j=0; j < columns; j++){
                // to start, set all values to -1
                Board[i][j] =- 1;
            }
        }
        // create a temp to store the number of rows already filled
        ArrayList<Integer> tempList = new ArrayList<>(filled*rows);
        int x = 0;
        // loop through the number of items filled and the rows
        for(int i = 0; i < filled; i++){
            for(int j = 0; j < rows; j++){
                // add x value to the temp
                tempList.add(x);
            }
            if(x == 0)
                x++;
            else
                x--;
        }
        int k = 0;
        // while the temp is not empty
        // loop through what has already been filled
        while(!(tempList.isEmpty())){
            for(int j = 0; j < filled; j++){
                // create a new random integer with the limit of the temp size
                int random = new Random().nextInt(tempList.size());
                // get a random value from the board then remove the random value
                Board[k][j] = tempList.get(random);
                tempList.remove(random);
            }
            k++;
        }
    }

    public void print(){
        System.out.println("-----------");
        // loop through the array
        // if the values at the board are not -1, print out the board values
        for(int i = 0; i < rows; i++){
            for(int j = 0; j < columns; j++){
                if(Board[i][j] != -1){
                    System.out.print(Board[i][j] + " ");
                }
            }
            System.out.println();
        }
        System.out.println("-----------");
        for(int k = 0; k < columns; k++){
            if(Board[1][k] != -1) {
                System.out.print(k + 1 + " ");
            }
        }
        System.out.println();
    }
    public static void main(String[] args){
        Scanner sc=new Scanner(System.in);
        int number_of_tubes = 0;
        int balls_in_tube = 0;
        int filled = 0;

        // if the length of the input is less than 3 print an error and exit
        if(args.length < 3){
            System.out.println("3 inputs needed, try again");
            System.exit(1);
        }

        number_of_tubes = Integer.parseInt(args[0]);
        balls_in_tube = Integer.parseInt(args[1]);
        filled = Integer.parseInt(args[2]);

        // number of tubes needs to be between 4 & 12
        while(number_of_tubes < 4 || number_of_tubes > 12){
            System.out.println(number_of_tubes + " number of tubes is not valid. Enter a value between 4 and 12:");
            number_of_tubes = sc.nextInt();
        }
        // number of balls needs to be between 4 & 8
        while(balls_in_tube < 4|| balls_in_tube > 8){
            System.out.println(balls_in_tube + " number of balls per tube is not valid. Enter a value between 4 and 8:");
            balls_in_tube = sc.nextInt();
        }

        while(filled < 2 || filled > number_of_tubes - 2){
            System.out.println(filled + " number of tubes filled is not valid. Enter a value between 2 and " + number_of_tubes + " minus 2:");
            filled = sc.nextInt();
        }

        TowersOfFourOrMore tower = new TowersOfFourOrMore(balls_in_tube, number_of_tubes, filled);
        tower.fill();
        System.out.println("Random Board:");
        tower.print();
        System.out.println();
        tower.solve_tower();
        System.out.println("Solved Board: ");
        tower.print();
    }
}
