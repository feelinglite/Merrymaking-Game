    String[] word = {"кот", "собака", "дерево", "машина"};
    String secretWord = word[random.nextInt(word.length)];

    StringBuilder mask = new StringBuilder();
    for (int i = 0; i < secretWord.length(); i++) {
        mask.append("_ ");
    }
    int lives = 6;

    while (lives > 0 && mask.indexOf("_") != -1) {
        System.out.println();
        System.out.println("Слово " + mask);
        System.out.println("Жизней " + lives);

        String letter = "";
        while (true) {
            System.out.println("Введите ровно одну букву: ");
            String input = scanner.nextLine();
            if (input.length() != 1) {
                System.out.println("Такой буквы нет");
                continue;
            }
            letter = input;
            break;
        }
        boolean quessend = false;
        for (int i = 0; i < secretWord.length(); i++) {
            if (secretWord.charAt(i) == letter.charAt(0)) {
                mask.setCharAt(i * 2, letter.charAt(0));
                quessend = true;
            }
        }
        if (quessend) {
            System.out.println("Буква найдена");

        } else {
            lives--;
            System.out.println("Такой буквы нет");
        }
    }

    System.out.println();
    if (lives == 0) {
        System.out.println("Вы проиграли. Слово было: " + secretWord);
    } else {
        System.out.println("Вы выиграли. Т.к слово было: " + secretWord);
    }
}
