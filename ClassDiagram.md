```mermaid

classDiagram

    Publicaçao "*" *-- "1" Entidade
    Publicaçao "*" *-- "1" Aluno
    Notificacao "*" *-- "1" Entidade
    Notificacao "*" *-- "1" Aluno
    Usuario <|.. Entidade
    Usuario <|.. Aluno
    Publicaçao o-- Tag
    Evento "*" *-- "1" Entidade
    AvaliacaoLocal <|..  Bebedouro
    AvaliacaoLocal <|.. Banheiro
    Bebedouro "1" *-- "*" BebedouroNota
    Banheiro "1" *-- "*" BanheiroNota

    <<Abstract>> Usuario
    <<Abstract>> AvaliacaoLocal

    class Aluno{
      -date DoB
      +criarPublicacao(): bool
      +cadastrarAluno(): bool
      +validarAluno(): bool
      +obterDetalhesUsuario(): object
    }

    class Entidade{
      +criarEvento(): bool
      +criarPublicacao(): bool
      +cadastrarEntidade(): bool
      +validarEntidade(): bool
      +obterDetalhesUsuario(): object
    }

    class Usuario{
      -int Id
      -guid GUID
      -string nome
      -string email
      -string documento
      +criarPublicacao()*: bool
      +obterDetalhesUsuario()*: object
    }

    class Evento{
      -int Id
      -guid GUID
      -string nome
      -date Data
      +editar(): bool
      +remover(): bool
      +criarEvento(): 
      +obterEventos(): list object
    }

    class Publicaçao{
      -int Id
      -guid GUID
      -date DataDeCriação
      -bool editado
      -string Texto
      -bool TemImagem
      -int QntdCurtidas
      -bool Anonimo
      +getURLImagem(): string
      +obterDetalhesPublicacao(): object
      +obterPublicacoesPorTag(): int
      +obterPublicacoesPorUsuario(): int
      +obterPublicacoesPorTexto(): int
      +obterPublicacoesUId(): int
      +validarPublicacao(): bool
      +adicionarDenuncia(): bool
      +adicionarAvaliacao(): bool
    }

    class Tag{
      -int Id
      -guid GUID
      -string nome
    }

    class AvaliacaoLocal{
      -int Id
      -guid GUID
      -string localidade
      -string ImagemURL
      -float mediaNota
      +AvaliarLocal()*: bool
    }

    class Bebedouro{
      -int tipo
      +AvaliarLocal(): bool
    }

    class Banheiro{
      -int genero
      -bool acessivelPCD
      +AvaliarLocal(): bool
    }

    class BebedouroNota{
      -guid GUID
      -int Id
      -int temperatura
      -int gosto
      -int fluxoDeAgua
      -int torneira
      -int botao
      -int gancho
      -string comentario
    }

    class BanheiroNota{
      -guid GUID
      -int Id
      -int limpeza
      -int tempoDeEspera
      -int conforto
      -int privacidade
      -int disponibilidadeDePapelHigienico
      -int disponibilidadeDePapelToalha
      -int disponibilidadeDeSabonete
      -int qualidadeDoEspelho
      -int qualidadeDaTorneira
      -int qualidadeDaDescarga
      -string comentario
    }

    class Notificacao{
      -int Id
      -guid GUID
      +obterNotificacaoPorUsuario(): list object
    }
```
