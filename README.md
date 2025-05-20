import java.util.Scanner; // Importa a ferramenta Scanner para ler entradas do usuário

public class SistemaBibliotecaFelipeMaia2A {
    
    // O método main é o ponto de entrada do programa
    public static void main(String[] args) {
        
        // Criação de uma instância de Biblioteca para manipular os livros e usuários
        Biblioteca biblioteca = new Biblioteca();

        // Criação de um objeto Scanner para ler dados do teclado
        Scanner scanner = new Scanner(System.in);
        
        // Variável para armazenar a opção escolhida pelo usuário
        String opcao;

        // Laço de repetição (loop) que vai continuar até o usuário escolher a opção de sair (0)
        do {
            // Exibe o menu de opções para o usuário
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
            
            // Lê a opção digitada pelo usuário
            opcao = scanner.nextLine();

            // Verifica qual opção o usuário escolheu
            switch (opcao) {
                
                case "1":
                    // Cadastro de Livro
                    System.out.print("ISBN: ");
                    String isbn = scanner.nextLine(); // Lê o ISBN do livro
                    System.out.print("Título: ");
                    String titulo = scanner.nextLine(); // Lê o título do livro
                    System.out.print("Autor: ");
                    String autor = scanner.nextLine(); // Lê o nome do autor
                    System.out.print("Ano: ");
                    int ano = Integer.parseInt(scanner.nextLine()); // Lê o ano e converte para inteiro
                    
                    // Tenta adicionar o livro na biblioteca
                    if (biblioteca.adicionarLivro(new Livro(isbn, titulo, autor, ano))) {
                        System.out.println("Livro cadastrado com sucesso.");
                    } else {
                        System.out.println("ISBN já cadastrado.");
                    }
                    break;

                case "2":
                    // Cadastro de Usuário
                    System.out.print("ID: ");
                    String id = scanner.nextLine(); // Lê o ID do usuário
                    System.out.print("Nome: ");
                    String nome = scanner.nextLine(); // Lê o nome do usuário
                    System.out.print("Email: ");
                    String email = scanner.nextLine(); // Lê o email do usuário
                    
                    // Tenta adicionar o usuário na biblioteca
                    if (biblioteca.adicionarUsuario(new Usuario(id, nome, email))) {
                        System.out.println("Usuário cadastrado.");
                    } else {
                        System.out.println("ID já utilizado.");
                    }
                    break;

                case "3":
                    // Cadastro de Administrador
                    System.out.print("ID: ");
                    String idAdm = scanner.nextLine(); // Lê o ID do administrador
                    System.out.print("Nome: ");
                    String nomeAdm = scanner.nextLine(); // Lê o nome do administrador
                    System.out.print("Email: ");
                    String emailAdm = scanner.nextLine(); // Lê o email do administrador
                    System.out.print("Cargo: ");
                    String cargo = scanner.nextLine(); // Lê o cargo do administrador
                    
                    // Tenta adicionar o administrador na biblioteca
                    if (biblioteca.adicionarAdministrador(new Administrador(idAdm, nomeAdm, emailAdm, cargo))) {
                        System.out.println("Administrador cadastrado.");
                    } else {
                        System.out.println("ID já utilizado.");
                    }
                    break;

                case "4":
                    // Empréstimo de Livro
                    System.out.print("ISBN do livro a emprestar: ");
                    String isbnEmp = scanner.nextLine(); // Lê o ISBN do livro a ser emprestado
                    
                    // Tenta emprestar o livro
                    if (biblioteca.emprestarLivro(isbnEmp)) {
                        System.out.println("Livro emprestado com sucesso.");
                    } else {
                        System.out.println("Livro não disponível ou não encontrado.");
                    }
                    break;

                case "5":
                    // Listar todos os livros cadastrados
                    for (Livro l : biblioteca.listarLivros()) {
                        System.out.println(l); // Chama o método toString de cada livro para exibir seus detalhes
                    }
                    break;

                case "6":
                    // Listar todos os usuários cadastrados
                    for (Usuario u : biblioteca.listarUsuarios()) {
                        System.out.println(u); // Chama o método toString de cada usuário para exibir seus detalhes
                    }
                    break;

                case "7":
                    // Listar todos os administradores cadastrados
                    for (Administrador a : biblioteca.listarAdministradores()) {
                        System.out.println(a); // Chama o método toString de cada administrador para exibir seus detalhes
                    }
                    break;

                case "0":
                    // Caso o usuário queira sair do programa
                    System.out.println("Saindo...");
                    break;

                default:
                    // Se o usuário digitar uma opção inválida
                    System.out.println("Opção inválida.");
            }
        } while (!opcao.equals("0")); // Repete o menu até o usuário escolher a opção de sair (0)

        scanner.close(); // Fecha o Scanner, liberando os recursos
    }
}
