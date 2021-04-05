# Síntese lógica:

- Apresentação: Vítor Bandeira.
- Objetivo da Síntese Lógica: transforma ".vhdl" em uma série de equações e mapear para uma descrição de netlist utilizando células padrão.
- Em resumo: Arquivo ".vhdl" + arquivo ".sdc" (timming constraints) -> arquivo ".v" (design netlist) 
- Ao final deve gerar: Netlist, scripts (para a síntese física futuramente) and reports (para garantir que o circuito esta funcionando). 


## Arquivo constraints.sdc:

- Define o período do clock 5ns.
- Evita que o reset seja utilizado na análise de atraso.
- Define a carga nas saídas do circuito.
- Setar clock, bordas de subida e descida, reset e capacitancia de saída.

## Arquivo synth.tcl:

- Informações (linhas):
  - 23-24 (bibliotecas usadas)
  - 59 - esforço leakage power
- Modificar (linhas): 
  - 15
  - 67 + 5
  - 80 + 5 constraints
  - 233 + 5

# Exemplo prático:

- help comando -> ajuda sobre comandos

~~~shell
# **baixar .zip 

cd testa-padrao
tcsh
source /scripts/set_cadence.csh
source /scripts/set_cadence_innovus161.csh

cd /synthesis
genus -files synth.tcl # criar um .tcl para nosso projeto

# **se der certo vai aparecer syntesis finished
# gera os arquivos setup.tcl: source innovus/busca_padrao.genus_setup.tcl e outro

# ao fechar a ferramenta se quiser abrir de novo para acessar os resultados:
source innovus/light8080.genus_setup.tcl

gui_show # abre a interface gráfica

# botao dir no nome proj -> open in -> schematic viewer
  # abre o esquematico da netlist com o mapeamento

# power -> report -> detailed report = ver reports - colocar no relatório

# timming -> worst slack = se negativo não atende as constraints (nao funciona corretamente) 
  # slack rise e fall devem ficar positivos
  # mudar arquivo de constraints (clock)
    # baixa clock de 2 para 10 ns e corrige o slack

# serão gerados reports no diretorio scripts
  # basta abri-los para verificar

report_area # report area valores

~~~