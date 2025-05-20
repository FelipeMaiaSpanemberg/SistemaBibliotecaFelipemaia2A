package poo.sistemabibliotecafelipemaia2a;

import java.util.ArrayList;
import java.util.List;

public class Biblioteca {

    private List<Livro> livros;
    private List<Usuario> usuarios;
    private List<Administrador> administradores;

    public Biblioteca() {
        livros = new ArrayList<>();
        usuarios = new ArrayList<>();
        administradores = new ArrayList<>();
    }

    public boolean adicionarLivro(Livro livro) {

        for (Livro l : livros) {
            if (l.getIsbn().equals(livro.getIsbn())) {
                return false;
            }
        }
        livros.add(livro);
        return true;
    }

    public boolean adicionarUsuario(Usuario usuario) {

        for (Usuario u : usuarios) {
            if (u.getId().equals(usuario.getId())) {
                return false;
            }
        }
        usuarios.add(usuario);
        return true;
    }

    public boolean adicionarAdministrador(Administrador administrador) {
        for (Administrador a : administradores) {
            if (a.getId().equals(administrador.getId())) {
                return false;
            }
        }
        administradores.add(administrador);
        return true;
    }

    public boolean emprestarLivro(String isbn) {
        for (Livro livro : livros) {
            if (livro.getIsbn().equals(isbn)) {

                if (livro.isDisponivel()) {
                    livro.setDisponivel(false);
                    return true;
                }
                return false;
            }
        }
        return false;
    }

    public List<Livro> listarLivros() {
        return livros;
    }

    public List<Usuario> listarUsuarios() {
        return usuarios;
    }

    public List<Administrador> listarAdministradores() {
        return administradores;
    }
}
