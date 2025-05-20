package poo.sistemabibliotecafelipemaiaspanemberg2a;

public class Livro {

private String isbn;
private String titulo;
private String autor;
private int ano;
private boolean disponivel;

public Livro(String isbn, String titulo, String autor, int ano) {
    this.isbn = isbn;
    this.titulo = titulo;
    this.autor = autor;
    this.ano = ano;
    this.disponivel = true;
}

public String getIsbn() {
    return isbn;
}

public String getTitulo() {
    return titulo;
}

public String getAutor() {
    return autor;
}

public int getAno() {
    return ano;
}

public boolean isDisponivel() {
    return disponivel;
}

public void setDisponivel(boolean disponivel) {
    this.disponivel = disponivel;
}

public String toString() {
    return titulo + " - " + autor + " (" + ano + ") [ISBN: " + isbn + "] " + (disponivel ? "[Disponível]" : "[Emprestado]");
}
}
