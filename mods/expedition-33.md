<p align="center"><img src="../assets/brand/banner.png" alt="SenseForge" width="100%"></p>

# SenseForge para Clair Obscur: Expedition 33

**Versão 0.1.0** · download em breve

Gatilhos adaptativos, lightbar e vibração do DualSense nativos no Expedition 33: parry dourado, mira livre com resistência no L2, R2 travado no combate e mais.

## O que o MOD faz

- Parry: lightbar dourada, motores e vibração nos gatilhos
- QTE perfeito: pulso branco
- Esquiva, golpe recebido, tiro da mira livre e ataque na exploração com cores próprias na lightbar
- R2 com trava no combate e L2 com resistência na mira livre
- Aba SenseForge no overlay do ReShade (tecla Home): presets, perfis Fraco/Médio/Forte e ajuste por efeito

## Requisitos

- Windows 10 ou 11 (64 bits)
- Clair Obscur: Expedition 33 na Steam
- Controle DualSense (PS5). Por cabo USB para tudo funcionar; por Bluetooth, gatilhos e lightbar funcionam, mas sem HD haptics e sem alto-falante
- ReShade 6.8+ com suporte a add-ons (passo a passo abaixo)

## Dependências

### UE4SS (RE-UE4SS) (3.0.1-1181-g83330635): já vem no zip

Lê os eventos de gameplay do jogo (parry, mira, golpes) e os entrega ao SenseForge. Já vem no zip, com o console desligado.

Site: <https://github.com/UE4SS-RE/RE-UE4SS> · Licença: MIT

### ReShade com suporte a add-ons (6.8.0 ou mais novo): **instale antes do MOD**

Carrega o SenseForge dentro do jogo e mostra a aba de ajustes (tecla Home). Precisa ser a versão "with full add-on support".

Site: <https://reshade.me> · Licença: BSD-3-Clause

1. Baixe em https://reshade.me a versão "with full add-on support" (o instalador avisa que é para jogos single-player).
2. Abra o instalador e escolha SandFall-Win64-Shipping.exe em Expedition 33/Sandfall/Binaries/Win64.
3. Escolha a API DirectX 10/11/12.
4. Na lista de efeitos, você pode desmarcar tudo: o SenseForge não precisa de shaders. Na lista de add-ons, nada é obrigatório.

## Desempenho e stutter

Ainda não medido com números. O SenseForge roda numa thread própria a 50 Hz e não toca na renderização; a medição A/B (vanilla vs MOD) entra na próxima versão deste guia.

- No boot há uma espera de 15 s antes de o SenseForge ligar, de propósito, para não disputar recursos com o carregamento do jogo.
- O pacote não faz dumps de objetos do UE4SS no boot (eles causavam um engasgo de alguns segundos e só servem a quem desenvolve).

## Incompatibilidades conhecidas

- **Dois SenseForge na pasta**: Se existir um senseforge.addon64 antigo junto do senseforge.expedition-33.addon64, o ReShade carrega os dois e aparecem duas abas. Apague o antigo.
- **DSX, DualSenseX, DualSenseY e DS4Windows**: Ferramentas que assumem o controle podem brigar com o SenseForge pelos gatilhos e pela lightbar. Feche-as enquanto joga.
- **Steam Input**: Pode continuar ligado; o SenseForge fala com o controle direto por HID. Se a lightbar piscar com a cor da Steam, desative o "Suporte a PlayStation" só para este jogo.
- **Outros mods UE4SS**: Funcionam juntos, desde que o mods.txt mantenha SenseForgeBridge : 1. Mods que reinstalem outra versão do UE4SS podem quebrar a ponte de eventos.
- **Overlays (RTSS, NVIDIA, Discord)**: Compatíveis: testado com RTSS e overlay da NVIDIA ativos.
- **Bluetooth**: Sem HD haptics e sem alto-falante (o Windows só expõe os 4 canais de áudio do DualSense por USB).

## Instalação

1. **Instale o ReShade com suporte a add-ons**, seguindo os passos da seção Dependências acima.
2. **Baixe o zip** deste MOD na tabela de downloads.
3. **Abra a pasta do jogo.** Na Steam, clique com o botão direito em *Clair Obscur: Expedition 33* → *Gerenciar* → *Ver arquivos locais*. Depois entre em `Sandfall/Binaries/Win64`, onde fica o `SandFall-Win64-Shipping.exe`.
4. **Extraia o conteúdo do zip** nessa pasta e aceite substituir os arquivos. A pasta fica assim:

   ```
   Win64/
   ├─ SandFall-Win64-Shipping.exe          (do jogo)
   ├─ dxgi.dll, reshade.ini                (do ReShade)
   ├─ dwmapi.dll                           (UE4SS)
   ├─ senseforge.expedition-33.addon64     (SenseForge)
   ├─ expedition33.sense.json              (perfil do jogo)
   ├─ senseforge_user.ini                  (seus ajustes)
   └─ ue4ss/
      ├─ UE4SS.dll, UE4SS-settings.ini
      └─ Mods/
         ├─ mods.txt
         └─ SenseForgeBridge/Scripts/main.lua
   ```

5. **Conecte o DualSense** antes de abrir o jogo. O cabo USB é recomendado.

## Primeiro uso

- Abra o jogo normalmente pela Steam. Nenhuma janela extra aparece.
- **Espere uns 15 segundos** depois do menu: o SenseForge liga depois desse tempo, de propósito.
- Aperte **Home** para abrir o overlay do ReShade e vá na aba **SenseForge**:
  - **Preset**: *Desligado* deixa o controle como no jogo original. *Preset 1, 2 e 3* guardam ajustes separados (por exemplo, um para jogar à noite com tudo mais leve).
  - **Perfil**: *Fraco*, *Médio* ou *Forte* preenchem as intensidades de uma vez. Se você mexer à mão, o perfil vira *Personalizado*.
  - **Status ao vivo**: mostra se o controle foi encontrado e o que o SenseForge está fazendo agora.
  - **Ajuste por efeito**: liga ou desliga cada efeito, muda a força de cada gatilho e tem um botão **Testar** para sentir o efeito na hora.
- Os ajustes são salvos sozinhos no `senseforge_user.ini`.

## Solução de problemas

| Sintoma | O que fazer |
|---|---|
| A aba SenseForge não aparece | Confira se o ReShade instalado é o **with full add-on support** e se o arquivo `senseforge.expedition-33.addon64` está na pasta `Win64`. |
| "Controle: não encontrado" | Conecte o DualSense antes de abrir o jogo e feche DSX, DS4Windows e programas parecidos. |
| Duas abas SenseForge | Apague o `senseforge.addon64` antigo. Fica só o `senseforge.expedition-33.addon64`. |
| Sem vibração HD nem som no controle | Isso só funciona por cabo USB. Em *Configurações de som do Windows*, o dispositivo "Wireless Controller" precisa estar ativo. |
| O efeito parece fraco | Em **Perfil**, escolha *Forte*. Para ir além do padrão, use *Gatilho L2/R2 → Máximo*. |

Se precisar de ajuda, abra uma *issue* neste repositório. Anexe o log de `%LOCALAPPDATA%\senseforge\logs\` (o arquivo mais recente) e o `ue4ss\UE4SS.log` da pasta do jogo.

## Desinstalação

Apague da pasta `Win64` os arquivos `senseforge.expedition-33.addon64`, `expedition33.sense.json`, `senseforge_user.ini` e a pasta `ue4ss/Mods/SenseForgeBridge`. Para remover também o UE4SS, apague o `dwmapi.dll` e a pasta `ue4ss`. O ReShade tem desinstalador próprio.

## English (short)

Clair Obscur: Expedition 33 DualSense MOD (adaptive triggers, lightbar, HD haptics). Install ReShade *with full add-on support*, extract the zip into `Sandfall/Binaries/Win64`, press **Home** and open the **SenseForge** tab.

---
<sub>MOD por Pedro Alves · SenseForge</sub>
