**Problema:** Um hospital precisa compartilhar dados de pacientes com pesquisadores que buscam monitorar os efeitos colaterais de medicamentos ou o avanço de epidemias. O hospital oculta o nome dos pacientes, mas mantém as datas exatas de nascimento e os CEPs dos pacientes. Um pesquisador consegue identificar de forma exclusiva um indivíduo cruzando essas duas informações com listas eleitorais ou comerciais de bancos de dados externos.

**Conceito utilizado:** Privacidade de dados pessoais (LGPD), descaracterização e anonimização de informações confidenciais.

**Solução:** Aplicar técnicas de descaracterização de dados confidenciais:

- Substituir a **data de nascimento exata** (dia/mês/ano) apenas pelo **ano de nascimento**.
- Substituir o **CEP detalhado** por uma representação regional mais genérica (ex: apenas os primeiros dígitos que indicam a cidade/estado).

**Resultado:** Os pesquisadores continuam tendo dados estatísticos úteis por faixa etária e região geográfica, mas torna-se impossível cruzar os dados para identificar individualmente os pacientes.

**Por que essa solução funciona:** A diluição da precisão dos dados pessoais quebra a capacidade de ligação exclusiva entre bancos de dados heterogêneos, protegendo a privacidade sem eliminar a utilidade científica do conjunto de dados agregados.

**O que preciso aprender com esse exemplo:** A ocultação do nome (pseudonimização simples) é insuficiente para garantir a privacidade se houver atributos quase-identificadores (como data de nascimento e CEP combinados) na base compartilhada.