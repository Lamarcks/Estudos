**Problema:** Uma clínica médica precisa gerenciar o agendamento de suas consultas de forma que tanto os médicos responsáveis quanto os respectivos pacientes sejam notificados automaticamente sobre marcações ou alterações de datas e horários, sem que os componentes do sistema fiquem dependentes e acoplados diretamente entre si.

**Conceito utilizado:** Padrão de Projeto Comportamental _Observer_ (_Subject_ e _Observers_).

**Solução:** Cria-se a interface `Observer` com um método genérico `update(String msg)`. A classe publicadora `Agendamento` (_Subject_) mantém uma lista dinâmica de observadores registrados e dispara as atualizações sequencialmente após preencher os dados de uma nova consulta.

```
import java.util.ArrayList;
import java.util.List;

// Interface Observer
interface Observer {
    void update(String mensagem);
}

// Classe Subject (Sujeito)
class Agendamento {
    private String data;
    private String horario;
    private String medico;
    private String paciente;
    private List<Observer> observadores = new ArrayList<>();

    public void adicionarObserver(Observer observer) {
        observadores.add(observer);
    }

    public void removerObserver(Observer observer) {
        observadores.remove(observer);
    }

    public void notificarObservers() {
        for (Observer observer : observadores) {
            observer.update("Novo agendamento: " + paciente + " com o médico " + medico + " no dia " + data + " às " + horario);
        }
    }

    public void agendarConsulta(String paciente, String medico, String data, String horario) {
        this.paciente = paciente;
        this.medico = medico;
        this.data = data;
        this.horario = horario;
        notificarObservers(); // Dispara o alerta após agendar
    }
}

// Classe Paciente (Observer)
class Paciente implements Observer {
    private String nome;
    public Paciente(String nome) { this.nome = nome; }
    @Override
    public void update(String mensagem) {
        System.out.println("Paciente " + nome + " recebeu a notificação: " + mensagem);
    }
}

// Classe Médico (Observer)
class Medico implements Observer {
    private String nome;
    public Medico(String nome) { this.nome = nome; }
    @Override
    public void update(String mensagem) {
        System.out.println("Médico " + nome + " recebeu a notificação: " + mensagem);
    }
}
```

**Resultado:** Ao executar o método `agendarConsulta()`, os pacientes e médicos cadastrados na lista recebem automaticamente as atualizações personalizadas no console, de forma sincronizada e imediata.

**Por que essa solução funciona:** A classe publicadora (`Agendamento`) não conhece os detalhes de implementação das instâncias de `Paciente` ou `Medico`. Ela conhece apenas a assinatura comum exigida pelo contrato da interface `Observer`, permitindo a propagação de eventos sem criar dependência rígida entre os objetos.

**O que preciso aprender com esse exemplo:**

- O padrão _Observer_ promove o **desacoplamento** entre publicadores (_Subjects_) e assinantes (_Observers_).
- É altamente escalável: novas classes interessadas (ex: secretárias ou faturamento) podem ser adicionadas posteriormente apenas implementando a interface `Observer`, sem a necessidade de reescrever ou alterar o código de agendamento principal.