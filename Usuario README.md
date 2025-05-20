package poo.sistemabibliotecafelipemaia2a;
public class Usuario {

    private String id;      
    private String nome;   
    private String email;  


    public Usuario(String id, String nome, String email) {
        this.id = id;       
        this.nome = nome;    
        this.email = email;  
    }

    
    public String getId() { return id; }          
    public String getNome() { return nome; }      
    public String getEmail() { return email; }   

   
    public String toString() {
      
        return nome + " (ID: " + id + ", Email: " + email + ")";
    }
}
