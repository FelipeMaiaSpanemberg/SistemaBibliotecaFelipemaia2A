package poo.sistemabibliotecafelipemaia2a;

public class Administrador {

    private String id;
    private String nome;
    private String email;
    private String cargo;

    public Administrador(String id, String nome, String email, String cargo) {
        this.id = id;
        this.nome = nome;
        this.email = email;
        this.cargo = cargo;
    }

    public String getId() {
        return id;
    }

    public String getNome() {
        return nome;
    }

    public String getEmail() {
        return email;
    }

    public String getCargo() {
        return cargo;
    }

    public String toString() {
        return nome + " (ID: " + id + ", Cargo: " + cargo + ")";
    }
}
