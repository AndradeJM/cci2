# Floorplanning:

- Objetivos: minimizar a área e o atraso.
- Arquivos de entrada: Netlist após a síntese lógica (busca_padrao.v) + timming constraints (busca_padrao.sdc) => busca_padrao.v
- Durante o Floorplanning:
  - Estimaremos o tamanho do chip
  - Disposição dos blocos lógicos.
  - I/O
  - Power Planning (roteamento de Gnd e Vdd).

  # Exemplo prático:

- help comando -> ajuda sobre comandos

~~~shell
cd testa-padrao
tcsh
source /scripts/set_cadence.csh
source /scripts/set_cadence_innovus161.csh

innovus -common_ui

cd synthesis

source physical/1_init.tcl # gera uma estimativa de área

source physical/2_power_plan.tcl # vai gerar trilhas de vdd e gnd

~~~
