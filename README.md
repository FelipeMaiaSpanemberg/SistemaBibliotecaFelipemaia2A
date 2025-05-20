package poo.sistemabibliotecafelipemaia2a;

import java.util.Scanner;

public class SistemaBibliotecaFelipeMaia2A {

    public static void main(String[] args) {
        Biblioteca biblioteca = new Biblioteca();
        Scanner scanner = new Scanner(System.in);
        String opcao;

        do {
            System.out.println("\n--- MENU ---");
            System.out.println("1. Cadastrar Livro");
            System.out.println("2. Cadastrar Usuario");
            System.out.println("3. Cadastrar Administrador");
            System.out.println("4. Emprestar Livro");
            System.out.println("5. Listar Livros");
            System.out.println("6. Listar Usuarios");
            System.out.println("7. Listar Administradores");
            System.out.println("0. Sair");
            System.out.print("Escolha uma opção: ");
            opcao = scanner.nextLine();

            switch (opcao) {
                case "1":
                    System.out.print("ISBN: ");
                    String isbn = scanner.nextLine();
                    System.out.print("Título: ");
                    String titulo = scanner.nextLine();
                    System.out.print("Autor: ");
                    String autor = scanner.nextLine();
                    System.out.print("Ano: ");
                    int ano = Integer.parseInt(scanner.nextLine());
                    if (biblioteca.adicionarLivro(new Livro(isbn, titulo, autor, ano))) {
                        System.out.println("Livro cadastrado com sucesso.");
                    } else {
                        System.out.println("ISBN já cadastrado.");
                    }
                    break;

                case "2":
                    System.out.print("ID: ");
                    String id = scanner.nextLine();
                    System.out.print("Nome: ");
                    String nome = scanner.nextLine();
                    System.out.print("Email: ");
                    String email = scanner.nextLine();
                    if (biblioteca.adicionarUsuario(new Usuario(id, nome, email))) {
                        System.out.println("Usuário cadastrado.");
                    } else {
                        System.out.println("ID já utilizado.");
                    }
                    break;

                case "3":
                    System.out.print("ID: ");
                    String idAdm = scanner.nextLine();
                    System.out.print("Nome: ");
                    String nomeAdm = scanner.nextLine();
                    System.out.print("Email: ");
                    String emailAdm = scanner.nextLine();
                    System.out.print("Cargo: ");
                    String cargo = scanner.nextLine();
                    if (biblioteca.adicionarAdministrador(new Administrador(idAdm, nomeAdm, emailAdm, cargo))) {
                        System.out.println("Administrador cadastrado.");
                    } else {
                        System.out.println("ID já utilizado.");
                    }
                    break;

                case "4":
                    System.out.print("ISBN do livro para emprestar: ");
                    String isbnEmprestimo = scanner.nextLine();
                    if (biblioteca.emprestarLivro(isbnEmprestimo)) {
                        System.out.println("Livro emprestado.");
                    } else {
                        System.out.println("Livro não disponível.");
                    }
                    break;

                case "5":
                    biblioteca.listarLivros().forEach(System.out::println);
                    break;

                case "6":
                    biblioteca.listarUsuarios().forEach(System.out::println);
                    break;

                case "7":
                    biblioteca.listarAdministradores().forEach(System.out::println);
                    break;

                case "0":
                    System.out.println("Saindo...");
                    break;
                default:
                    System.out.println("Opção inválida!");
            }
        } while (!opcao.equals("0"));
    }
}
