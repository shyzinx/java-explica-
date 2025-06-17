import java.io.FileWriter; // Importa a classe para escrever em arquivos
import java.io.IOException; // Importa a classe para tratar erros de I/O
import java.util.Scanner; // Importa a classe para ler dados do usuário

public class CadastroProdutos {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in); // Cria scanner para entrada de dados
        String continuar = "s"; // Controla o loop de cadastro

        try {
            FileWriter writer = new FileWriter("produtos.txt", true); // Cria FileWriter no modo append (não sobrescreve o arquivo)

            while (continuar.equalsIgnoreCase("s")) { // Enquanto o usuário quiser cadastrar
                System.out.print("Digite o nome do produto: ");
                String nome = scanner.nextLine(); // Lê o nome do produto

                System.out.print("Digite o preço do produto: ");
                double preco = Double.parseDouble(scanner.nextLine()); // Lê e converte o preço para double

                writer.write("Nome: " + nome + ", Preço: " + preco + "\n"); // Escreve os dados no arquivo

                System.out.print("Deseja cadastrar outro produto? (s/n): ");
                continuar = scanner.nextLine(); // Pergunta se quer continuar
            }

            writer.close(); // Fecha o FileWriter
            System.out.println("Produtos cadastrados com sucesso!");

        } catch (IOException e) {
            System.out.println("Erro ao escrever no arquivo: " + e.getMessage()); // Trata erro de escrita
        }

        scanner.close(); // Fecha o Scanner
    }
}
