**Problema:** Um usuário precisa executar um aplicativo pesado de restauração de imagens que exige 100 MB de espaço de memória, ao mesmo tempo em que usa um editor de texto de 60 MB. Entretanto, a máquina possui apenas 145 MB de RAM física disponível.

**Conceito utilizado:** Gerenciamento de **Memória Virtual por Paginação Sob Demanda**.

**Solução:** O gerenciador de memória virtual do S.O. mapeia os aplicativos em blocos lógicos menores (páginas):

1. Aloca os 100 MB do aplicativo de imagens inteiramente na RAM física.
2. Aloca apenas a parte ativa do editor de texto (45 MB) na RAM física restante.
3. O restante do código do editor de texto (15 MB) permanece em disco rígido.
4. Quando as instruções que estão no disco forem chamadas pelo processador, o S.O. faz a troca de páginas (_page fault_) trazendo os dados para a RAM e enviando páginas não utilizadas de volta ao disco.

**Resultado:** O usuário consegue trabalhar nos dois programas em paralelo de maneira transparente, sem receber avisos de memória insuficiente, apesar de ultrapassar o limite físico em 15 MB.

**Por que essa solução funciona:** Os programas raramente utilizam 100% de seu código fonte a cada segundo de execução. A paginação sob demanda tira proveito disso para carregar fisicamente na RAM apenas as partes de código estritamente necessárias para a instrução em andamento.

**O que preciso aprender com esse exemplo:** A paginação permite que o tamanho lógico ocupado pelas aplicações seja maior do que a RAM física instalada. Divisões lógicas menores e idênticas (páginas) dão flexibilidade ao sistema operacional para otimizar o uso da memória real de forma muito mais dinâmica do que o _swapping_ completo de processos.
