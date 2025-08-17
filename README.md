# Conceitos-de-Programa-o-Orientada-a-Objetos
SEGUNDO DESAFIO DA DIO "HANGMAN".

# Código Principal:

package br.com.dio.hangman;

import br.com.dio.hangman.model.HangmanChar;
import br.com.dio.hangman.model.HangmanGame;

import java.util.Sacnner;
import java.util.stream.Stream;

public class Main {

    private final Scanner scanner = new Scanner(System.in);
    
    public static void main(String... args) {
        var characters = Stream.of(args)
                .map(a -> a.toLowerCase().charAt(0))
                .map(HangmanChar::new).toList();
        System.out.println(characters);
        var hangmanGame = new HangmanGame(characters);
        System.out.println("Bem vindo ao jogo da forca, tente adivinhar a palavra boa sorte!");
        System.out.println(hangmanGame); 
        System.out.println("Selecione uma das opções:");
        System.out.println("1 - Informar uma letra");
        System.out.println("2 - Informar status do jogo");
        System.out.println("3 - Sair do jogo");
        while(true){
            var option = scanner.nextInt();
            switch (option) {
                case 1 -> {
                    System.out.println("Informe uma letra:");
                    var letter = scanner.next().charAt(0);
                    hangmanGame.inputCharacter(letter);
                }
                case 2 -> System.out.println(hangmanGame);
                case 3 -> {
                    System.out.println("Obrigado por jogar!");
                    return;
                }
                default -> System.out.println("Opção inválida");
            }
        }
    }

}
