package poo.sistemabibliotecafelipemaiaspanemberg2a;

import java.util.Scanner;

public class SistemaBibliotecaFelipeMaiaSpanemberg2A {
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
                        System.out.println("Livro emprestado com sucesso.");
                    } else {
                        System.out.println("Livro não disponível ou não encontrado.");
                    }
                    break;

                case "5":
                    System.out.println("\nLista de Livros:");
                    for (Livro livro : biblioteca.listarLivros()) {
                        System.out.println(livro);
                    }
                    break;

                case "6":
                    System.out.println("\nLista de Usuários:");
                    for (Usuario usuario : biblioteca.listarUsuarios()) {
                        System.out.println(usuario);
                    }
                    break;

                case "7":
                    System.out.println("\nLista de Administradores:");
                    for (Administrador administrador : biblioteca.listarAdministradores()) {
                        System.out.println(administrador);
                    }
                    break;

                case "0":
                    System.out.println("Saindo...");
                    break;

                default:
                    System.out.println("Opção inválida.");
                    break;
            }
        } while (!opcao.equals("0"));

        scanner.close();
    }
}
