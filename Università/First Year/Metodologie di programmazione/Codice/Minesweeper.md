
# Classe GameField
```java
package minesweeper;

import java.util.Arrays;

import java.util.Random;

public class GameField {

	private int[][] field;
	
	private int nMines;

	public GameField(int N, int M, int nMines) {

		field = new int[N][M];
	
		this.nMines = nMines;

		placeMines();

	}

	private void placeMines() {

		Random rand = new Random();

		int placedMines = 0;

		while (placedMines < nMines) {

			int x = rand.nextInt(field.length);

			int y = rand.nextInt(field[0].length);

			if (field[x][y] != -1) {

				field[x][y] = -1;

				placedMines++;

			}

		}

	}

	@Override

	public String toString() {

		String result = new String();

		for (int i=1; i<field.length; i++) {

			for (int j=1; j<field[i].length; j++) {

			}

		}

	}

}
```

# classe Main
```java
package minesweeper;

public class Main {

	public static void main(String[] args) {

		GameField gameField = new GameField(10, 20, 12);

		System.out.println(gameField.toString());

	}

}
```