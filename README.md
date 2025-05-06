Violações Identificadas

1. Violação do SRP (Single Responsibility Principle)
Local: Classe GerenciadorBiblioteca
Problema: A classe possui múltiplas responsabilidades:

Gerenciar livros, usuários e empréstimos

Enviar e-mails e SMS

Calcular multas

Uma classe deve ter apenas um motivo para mudar.

Se houver alterações em notificações (ex.: adicionar WhatsApp), a classe precisará ser modificada.



2. Violação do OCP (Open/Closed Principle)
Local: Métodos RealizarEmprestimo e RealizarDevolucao
Problema: Se novas regras de empréstimo (ex.: limite de livros por usuário) ou novos tipos de notificação forem adicionados, o código precisará ser modificado.

O princípio diz que classes devem estar abertas para extensão, mas fechadas para modificação.

Deveria ser possível adicionar novos comportamentos sem alterar o código existente.




3. Violação do DIP (Dependency Inversion Principle)
Local: Métodos EnviarEmail e EnviarSMS acoplados diretamente em GerenciadorBiblioteca.
Problema: A classe depende de implementações concretas (e-mail/SMS) em vez de abstrações.

Depender de abstrações (interfaces) facilita a troca de serviços (ex.: usar um serviço de notificação externo).



4. Violação do ISP (Interface Segregation Principle)
Local: Não há interfaces, mas se existissem, uma única interface INotificacao com EnviarEmail e EnviarSMS forçaria classes a implementar métodos não usados.

Interfaces devem ser específicas para evitar que classes implementem métodos desnecessários.




5. Violações de Clean Code
Problemas identificados:

Nomes pouco descritivos: AdicionarLivro poderia ser CadastrarLivro.

Métodos longos: RealizarEmprestimo e RealizarDevolucao fazem muitas coisas.

Código repetitivo: Verificações de null poderiam ser encapsuladas.

Tratamento de erros inadequado: Retornar -1 para indicar erro não é claro.
