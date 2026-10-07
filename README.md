📱 **Projeto iPad 4 (iOS 10.3.4): Customização e Sobrevivência Legada em 2026**

🎯 **Objetivos Iniciais do Projeto**

Transformar um iPad 4 (32-bits, chip Apple A6X, 1 GB de RAM) rodando o iOS 10.3.4 dispositivo independente e livre de distrações, unindo as funções de:

- Kindle (leitura)
  
- iPod/MP3
  
- Mini TV/Stramings

Permitindo uma 'desconexão' do celular durante o momento de lazer.


🛠️ **Fase 1: Jailbreak & Infraestrutura Base**

O primeiro grande desafio foi contornar a expiração de certificados web no Safari do iOS 10. A instalação direta via navegador falhou, exigindo uma abordagem baseada no  computador.

•	**Método Utilizado:** Instalação Semi-Tethered via 3uTools (PC).

•	**Ferramenta de Jailbreak:** h3lix (Patched RC6).

•	**Resultado:** SUCESSO. O ambiente do Cydia foi estabelecido, e o comportamento do Jailbreak Semi-Tethered foi dominado (exigindo o disparo do Kickstart Production no app h3lix após reinicializações do sistema).

•	**Infraestrutura de Injeção de Pacotes:** Instalação do AppSync Unified (via Cydia/Filza) para permitir a validação e o funcionamento de lojas e aplicativos alternativos criados pela comunidade legada.


🎨 **Fase 2: Interface Visual & Ajustes de Performance**

Para atingir o visual roxo e minimalista desejado, focou-se em tweaks de alto rendimento e baixo consumo de memória RAM.

🟢 **O que deu CERTO (Tweaks Instalados e Mantidos)**

•	**Eclipse 4 (iOS 10)**: Engine de modo escuro que aplicou a identidade visual roxa em todo o sistema. (Nota de correção: Foi necessário desativá-lo especificamente no aplicativo nativo da Câmera para evitar telas pretas/crashes).

•	**NoSlowAnimations / Speed Intensifier**: Tweaks de aceleração que removeram o atraso das animações nativas da Apple, devolvendo agilidade ao iPad 4.

•	**Horseshoe**: Unificou e modernizou a Central de Controle em uma única página limpa.

•	**Priority Hub & TinyBar**: Combo que transformou as notificações volumosas do iOS 10 em banners minimalistas e organizados por ícones.

•	**Filza File Manager**: Gerenciador de arquivos essencial para manutenção do sistema, instalação de arquivos .deb e manipulação de registros.

•	**AppDrop**: Loja alternativa instalada via repositório de comunidade (https://github.io), permitindo baixar arquivos .ipa históricos de 2017 sem exigir login oficial da Apple.

•	**HSWidgets**: Motor de widgets nativos que permitiu fixar com sucesso um relógio digital e fotos customizadas diretamente na tela inicial.

•	**YouPiP / YouTube Original Plus**: Tweak responsável por liberar a reprodução em segundo plano (Background Playback), permitindo minimizar qualquer app de mídia e continuar ouvindo o áudio no trabalho.

•	**PreferenceLoader & Cydia Substrate:** Injeção de código e dependências de sistema para que todos os tweaks apareçam e sejam configuráveis na aba Ajustes do iPad.

🔴 **O que deu ERRADO & Foi Removido (Peso Morto)**

•	**iWidgets / Xen HTML / Pacotes da Evelyn (EW.WdgtPack.4 e LS EW4)**: Motores baseados em HTML/JavaScript [iWidget Pack Sch 3]. Causaram extrema lentidão, instabilidade e reinícios forçados (crashes) devido ao limite físico de 1 GB de RAM do iPad 4.

•	**Donkey Kong Animation Pack & M2 iWidgets Pack:** Pacotes de customização que corromperam o banco de dados do Cydia (dpkg/info), gerando erros vermelhos (sub-process dpkg-deb returned error exit status 2). O problema foi resolvido cirurgicamente limpando os diretórios via Filza e editando manualmente as linhas corrompidas no arquivo /var/lib/dpkg/status.

•	**LockscreenXI (iOS 10) & Springtomize 4:** Falharam ao tentar redimensionar ou centralizar o relógio da tela de bloqueio nativa devido à falta de servidores de licença ativos em 2026.


🎵 **Fase 3: A Luta pelo Streaming (Música & Vídeos)**

A maior barreira do projeto foi a mudança nos protocolos de segurança (SSL/TLS 1.3) e nos servidores de autenticação modernos das grandes empresas, inviabilizando logins tradicionais em dispositivos de 32-bits.

❌ **Testes de Áudio e Vídeo Online - FALHOU**

•	**Youtube e Spotify Oficial ou Versões Modificadas (Spotilife / SpotiApp / arquivos .deb):** As APIs de servidores antigos do Spotify e do YouTube foram desativadas pelas plataformas para apps de 32 bits no iOS 10, impedindo o login e o carregamento do catálogo, mesmo com o uso de tweaks.

•	**Aplicativos de Clima (AccuWeather, CARROT, Yahoo Weather):** Versões de 2017 baixadas pela AppDrop fecham sozinhos ou não carregam dados porque as APIs de clima atuais não conversam mais com o código do iOS 10.

•	**Tentativa com Navegador Web (Safari/Safari Plus):** O motor de busca (WebKit) do iOS 10 não conseguia processar as páginas modernas do YouTube Music/Spotify, gerando lentidão extrema e erros de certificados HTTPS.


❌ **Servidor Doméstico (Jellyfin e Acesso Remoto) - FALHOU**

•	**A Tentativa do Jellyfin + ngrok / Tailscale:** O servidor Jellyfin foi configurado no notebook para tentar servir como central de streaming privada para o iPad.

•	**Por que falhou no iPad:** A interface web do Jellyfin é muito pesada para a memória RAM (1 GB) e para o processador A6X do iPad 4. A criptografia de túneis remotos (ngrok) somada ao carregamento das capas exigia demais do hardware, resultando em fechamentos repentinos (crashes).

•	**Destino do Jellyfin:** O Jellyfin foi mantido exclusivamente no notebook/PC para uso local em outros dispositivos, sendo descartado do iPad.


🎯 **Soluções Definitivas Encontradas (Onde Tudo Deu Certo)**

Após contornar o uso de navegadores e servidores pesados, a solução foi concentrada em aplicativos e arquivos locais leves:

**Músicas Offline (nPlayer)**

•	**Extração das Músicas:** Uso de ferramentas web como o SpotDown para baixar playlists do Spotify em MP3 com capas e tags completas.

•	**Transferência sem Fio:** Uso do recurso Web Transfer (Wi-Fi) nativo do nPlayer no iPad. Pelo navegador do computador, as faixas foram enviadas via IP local diretamente para a memória do iPad, dispensando cabos ou servidores.

**TV ao Vivo (M3U Customizada)**

•	**Substituição do GSE Smart IPTV pelo nPlayer:** O GSE fechava ao carregar listas M3U públicas completas de 500+ canais por falta de memória RAM.

• **Arquivo M3U Leve (favoritos.m3u):** Criação de uma lista personalizada em formato de texto contendo apenas os 7 canais favoritos.

• **Resultado:** Carregamento estável no nPlayer, sem travamentos e com troca rápida de canais.


📈 **Status Atual do Dispositivo**

•	Sistema Operacional: iOS 10.3.4 (Jailbreak h3lix Semi-Tethered ativo).

•	Estabilidade: Alta. Após a remoção de tweaks em HTML, o sistema parou de reiniciar sozinho.

•	Interface: Concluída (Tema Escuro/Roxo com widgets de fotos e relógio ativos via HSWidgets).

•	Central Multimídia: nPlayer (executando áudio em segundo plano com suporte a arquivos locais e M3U). Rodando via HLS nativo

•	Status das Conexões: Dispositivo independente, sem dependência do notebook ligado ou de servidores remotos ativados.
