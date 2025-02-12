# AdvancedObjectDetector - Documentação

## Autor: Dr. Dheiver Francisco Santos

---

### Descrição do Projeto

O **AdvancedObjectDetector** é uma classe Python avançada desenvolvida para realizar detecção de objetos em imagens e vídeos com alta precisão. Ele utiliza a API do Roboflow (`inference_sdk`) para realizar inferências baseadas em modelos pré-treinados ou personalizados. O sistema é modular, permitindo processamento de imagens individuais, vídeos e até mesmo integração com múltiplos modelos.

Este projeto foi projetado para ser flexível, robusto e fácil de usar, com foco em aplicações práticas como monitoramento de objetos, análise de dados visuais e automação industrial.

---

### Funcionalidades Principais

1. **Detecção de Objetos em Imagens**:
   - Processa imagens estáticas e salva os resultados (imagem anotada e metadados JSON).
   - Suporte para ajuste de limiar de confiança (`confidence_threshold`).

2. **Detecção de Objetos em Vídeos**:
   - Processa vídeos frame a frame, aplicando detecção de objetos em tempo real.
   - Salva o vídeo processado com caixas delimitadoras e rótulos.

3. **Pré-processamento Avançado**:
   - Normalização de cores, equalização de histograma e remoção de ruído para melhorar a qualidade da entrada.

4. **Non-Maximum Suppression (NMS)**:
   - Remove caixas delimitadoras sobrepostas para reduzir falsos positivos.

5. **Visualização Interativa**:
   - Exibe imagens processadas usando Matplotlib para análise detalhada.

6. **Thread-Safety**:
   - Implementado com bloqueios (`threading.Lock`) para garantir operações seguras em ambientes multithread.

7. **Relatórios Detalhados**:
   - Gera arquivos JSON com informações sobre as detecções, incluindo coordenadas das caixas delimitadoras, classes detectadas e níveis de confiança.

---

### Requisitos de Instalação

Para executar este projeto, você precisará dos seguintes pacotes instalados:

```bash
pip install inference-sdk opencv-python matplotlib numpy
```

Além disso, certifique-se de ter acesso à API do Roboflow e um modelo treinado disponível para inferência.

---

### Estrutura do Código

A classe `AdvancedObjectDetector` é composta pelos seguintes métodos principais:

#### 1. **`__init__(self, api_key: str, api_url: str)`**
   - Inicializa o cliente de inferência com a chave de API e URL fornecidos.

#### 2. **`load_image(self, image_path: str) -> np.ndarray`**
   - Carrega uma imagem do disco para processamento.

#### 3. **`detect_objects(self, image: np.ndarray, model_id: str) -> list`**
   - Realiza a inferência em uma imagem usando o modelo especificado.

#### 4. **`draw_detections(self, image: np.ndarray, predictions: list, confidence_threshold: float) -> tuple`**
   - Desenha caixas delimitadoras e rótulos nas detecções, filtrando por limiar de confiança.

#### 5. **`process_image(self, image_path: str, model_id: str, confidence_threshold: float) -> dict`**
   - Processa uma única imagem, salva os resultados e retorna um resumo.

#### 6. **`process_video(self, video_path: str, model_id: str, output_path: str, confidence_threshold: float)`**
   - Processa um vídeo frame a frame, salvando o resultado em um novo arquivo.

#### 7. **`show_image(self, image: np.ndarray)`**
   - Exibe uma imagem processada usando Matplotlib.

---

### Como Usar

#### 1. Configuração Inicial

Antes de executar o código, configure as variáveis abaixo no método `main()`:

- `API_KEY`: Sua chave de API do Roboflow.
- `MODEL_ID`: ID do modelo que deseja usar para inferência.
- `IMAGE_PATH`: Caminho para a imagem de entrada.
- `VIDEO_PATH` (opcional): Caminho para o vídeo de entrada.
- `OUTPUT_VIDEO_PATH` (opcional): Caminho para salvar o vídeo processado.

#### 2. Executando o Código

Execute o script diretamente:

```bash
python advanced_object_detector.py
```

O programa irá processar a imagem ou vídeo especificado e exibir os resultados na tela.

---

### Exemplo de Saída

#### Para Imagens:
- Uma janela interativa será exibida com a imagem processada, contendo caixas delimitadoras e rótulos.
- Um arquivo JSON será gerado com informações detalhadas sobre as detecções.

#### Para Vídeos:
- Um novo vídeo será salvo no caminho especificado, contendo as detecções em cada frame.

---

### Melhorias Futuras

1. **Treinamento Personalizado**:
   - Treinar modelos específicos para domínios de interesse pode aumentar ainda mais a precisão.

2. **Integração com GPUs**:
   - Execute o código em um ambiente com GPU para acelerar o processamento.

3. **Interface Gráfica**:
   - Desenvolver uma interface gráfica para facilitar o uso por usuários não técnicos.

4. **Suporte para Múltiplos Modelos**:
   - Permitir a seleção dinâmica de diferentes modelos para diferentes tipos de objetos.

---

### Contato

Para dúvidas, sugestões ou colaborações, entre em contato com o autor:

- **Nome**: Dr. Dheiver Francisco Santos
- **E-mail**: [dheiver.santos@gmail.com](mailto:dheiver.santos@gmail.com)

---

### Licença

Este projeto está licenciado sob a **MIT License**, o que significa que você pode usá-lo, modificá-lo e distribuí-lo livremente, desde que mantenha os créditos ao autor original.

---

### Agradecimentos

Agradeço ao Roboflow pela API poderosa e aos frameworks de visão computacional que tornaram este projeto possível.
