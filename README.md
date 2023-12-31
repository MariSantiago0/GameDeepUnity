# GameDeepUnity
[![Unity](https://img.shields.io/badge/Unity-2022.2.16f1-blue)](https://unity3d.com/get-unity/download/archive)

<p>Músicas escolhidas para a inspiração do jogo:</p>
<strong>
Não creio mais em nada - Paulo Sérgio <Br>
Don't fear the Reaper - Blue Öyster Cult <Br>
Volta e meia - O terno <Br>
</strong>
<br>
<img src="imgs/chegada.png">
<h1>Tópicos</h1>
<ul>
 <li>
  Visão Geral
 <li>
  Requisitos
 </li>
 <li>
  Instalação
 </li>
 <li>
  Como jogar
  <li>
   Códigos
    <ul>
     <li>
      Código do Jogador
      <li>
      Código da Camera
      <li>
      Código dos Obstáculos
      <li>
      Código de troca de cena no Unity
    </ul>
 </li>
</ul>

<h2>Visão Geral</h2>
<img src="imgs/meio.png">
<h3>O jogo consiste em o jogador desviar dos obstáculos sem encostar; no entanto, se encostar, uma vida das suas 3 vidas é perdida. Cada vez que as cores dos obstáculos mudam, a velocidade deles diminui. Nosso jogo reflete o quão difícil pode ser no começo, mas tudo fica mais fácil se você se mostrar consistente e disciplinado.</h3>

<br><br>

<h2>Vídeo do jogo em execução</h2>

 https://youtu.be/Bb-MpDsUD34?si=tg6H9x_H9vhBwe8U

<h2>Requisitos</h2>
<p>
Antes de começar, certifique-se de ter os seguintes requisitos instalados:

- Unity versão 2022.2.16f1 ou superior
</p>

<br><br>

## Instalação

Siga as etapas abaixo para executar o jogo em sua máquina local:

1. Baixe os arquivos do jogo a partir [deste link](https://drive.google.com/file/d/1chjrV-hBKi7DeC7_l8oeSUsTkz-_tqKW/view?usp=drive_link).
2. Abra o projeto Unity utilizando a versão especificada nos requisitos.
3. Explore os arquivos do jogo para entender a estrutura e os ativos utilizados.

<br><br>

## Como Jogar

Siga as instruções abaixo para jogar o jogo:

1. Execute o jogo no Unity para começar a jogar.
2. Utilize as teclas de seta ou as teclas WASD para controlar o movimento do carro.
3. Desvie dos obstáculos e tente alcançar a linha de chegada da segunda fase sem perder suas vidas.

<br><br>


<h1>Códigos do Jogador</h1>
<img src="imgs/jogador.png">

<h2> Movimentação</h2>
<p>
<strong>Este é um script de controle do jogador para um jogo em 3D usando o motor Unity. Aqui está uma explicação básica de algumas partes do código:</strong><br>

- `public float speed = 10.0f;` : Esta é a velocidade de movimento do personagem.
- `public float airVelocity = 8f;` : Esta é a velocidade do personagem enquanto ele está no ar.
- `public float gravity = 10.0f;` : Esta é a força da gravidade aplicada ao personagem.
- `public float maxVelocityChange = 10.0f;` : Esta é a mudança máxima de velocidade que o personagem pode ter.
- `public float jumpHeight = 2.0f;` : Esta é a altura que o personagem pode pular.
- `public float maxFallSpeed = 20.0f;` : Esta é a velocidade máxima de queda do personagem.
- `public float rotateSpeed = 25f;` : Esta é a velocidade com que o personagem gira.
- `private Vector3 moveDir;` : Esta é a direção em que o personagem se move.
- `public GameObject cam;` : Este é o objeto da câmera que segue o personagem.
- `private Rigidbody rb;` : Este é o corpo rígido do personagem, usado para aplicar forças físicas.

<br><br><br>

O método `Start()` é chamado no início do jogo. Ele obtém a distância até o chão.<br>
O método `IsGrounded()` verifica se o personagem está no chão.<br>
O método `Awake()` é chamado quando o script é carregado. Ele obtém o componente Rigidbody do personagem e desativa a rotação e a gravidade automáticas.<br>
O método `FixedUpdate()` é chamado a cada quadro fixo (frame). Ele controla o movimento e a rotação do personagem, aplica a força da gravidade e permite ao personagem pular.<br>
O método `Update()` é chamado uma vez por quadro (frame). Ele obtém os inputs do usuário para mover o personagem.<br>
</p>

<br><br>

<h2>Perder vida ao colidir</h2>
<p>
 <strong>Este é um script de controle de vida do jogador caso o jogador colida com um obstáculo. Aqui está uma explicação básica de algumas partes do código:</strong> 
<br><br>
 
- `public int vidas = 3;` : Este é o número inicial de vidas do personagem.
- `void OnCollisionEnter(Collision collision)` : Este método é chamado quando o personagem colide com outro objeto. O objeto com o qual o personagem colidiu é passado como um parâmetro.
- `if (collision.gameObject.CompareTag("obstaculos"))` : Esta linha verifica se o objeto com o qual o personagem colidiu tem a tag "obstaculos". Se tiver, o código dentro das chaves `{}` será executado.
- `vidas--;` : Esta linha diminui o número de vidas do personagem em 1.
- `Debug.Log("Vida perdida! Vidas restantes: " + vidas);` : Esta linha imprime uma mensagem no console do Unity informando que uma vida foi perdida e quantas vidas restam.
- `if (vidas <= 0)` : Esta linha verifica se o número de vidas do personagem é menor ou igual a zero. Se for, o código dentro das chaves `{}` será executado.
- `Debug.Log("Game Over!");` : Esta linha imprime uma mensagem no console do Unity informando que o jogo acabou.
- `#if UNITY_EDITOR UnityEditor.EditorApplication.isPlaying = false; #else Application.Quit(); #endif` : Este bloco de código termina o jogo. Se o jogo estiver sendo executado no editor Unity, ele irá parar a reprodução. Se o jogo estiver sendo executado fora do editor, ele irá fechar a aplicação.
</p>

<br>

<h1>Código dos Obstáculos</h1>
<img src="imgs/meio2.png">
<img src="imgs/movel.png">
<h2>Código da Parede móvel (WallMoveable)</h2>
<img src="imgs/paredeobs.png">
<img src="imgs/wallmoveable.png">
<p>
  
- `public bool isDown = true;` : Esta variável determina se a parede começa em uma posição baixa. Se a parede não começar em uma posição baixa, você deve modificar para false.
- `public bool isRandom = true;` : Esta variável determina se a parede deve se mover para cima e para baixo de maneira aleatória.
- `public float speed = 2f;` : Esta é a velocidade com que a parede se move.
<br><br><br>
- `void Awake()` : Este método é chamado quando o script é carregado. Ele obtém a altura da parede e a posição inicial da parede.
- `void Update()` : Este método é chamado uma vez por quadro (frame). Ele controla o movimento da parede. Se a parede estiver em uma posição baixa, ela se moverá para cima. Se a parede estiver em uma posição alta, ela se moverá para baixo.
- `IEnumerator WaitToChange(float time)` : Esta função faz com que a parede espere por um certo tempo antes de mudar de direção. Se a variável `isRandom` for verdadeira e a parede estiver em uma posição alta, a função pode decidir aleatoriamente se a parede deve começar a se mover para baixo ou não.
- `IEnumerator Retry(float time)` : Esta função verifica periodicamente se a parede pode começar a se mover para baixo. A verificação ocorre a cada 1,25 segundos.
</p>

<br>

<h2>Código do Obstáculo móvel (MoveableWall) </h2>
<img src="imgs/movelobs.png">
<img src="imgs/moveablewall.png">
<p>
 <br>
 
- `public class MovableObs : MonoBehaviour`: Esta linha define uma nova classe chamada `MovableObs` que herda de `MonoBehaviour`, que é a classe base de onde todos os scripts Unity derivam.
- `public float distance = 5f;`: Define a distância que o objeto se move.
- `public bool horizontal = true;`: Define se o movimento é horizontal ou vertical.
- `public float speed = 3f;`: Define a velocidade do movimento do objeto.
- `public float offset = 0f;`: Permite modificar a posição inicial do objeto.
- `private bool isForward = true;`: Define se o movimento é para fora.
- `private Vector3 startPos;`: Armazena a posição inicial do objeto.
<br><br><br>
- `void Awake()`: É uma função do Unity chamada quando o script é carregado. Aqui, a posição inicial do objeto é armazenada e o deslocamento é aplicado à posição inicial.
- `void Update()`: É uma função do Unity chamada uma vez por frame. Aqui, o objeto é movido para frente e para trás ao longo do eixo x (se `horizontal` for verdadeiro) ou z (se `horizontal` for falso) entre sua posição inicial e sua posição inicial mais a distância definida.
</p>

<br>

<h1>Código da Câmera</h1>
<img src="imgs/camera.png">
<p>
<br>

- `public class CameraManager  : MonoBehaviour`: Esta linha define uma nova classe chamada `CameraManager` que herda de `MonoBehaviour`, que é a classe base de onde todos os scripts Unity derivam.
- `public float followSpeed = 3;`: Define a velocidade com que a câmera segue o jogador.
- `public float mouseSpeed = 2;`: Define a velocidade com que a câmera gira quando o mouse é movido.
- `public float cameraDist = 3;`: Define a distância entre a câmera e o jogador.
- `public Transform target;`: Armazena a referência ao jogador que a câmera deve seguir.
  <br><br><br>
- `public void Init()`: É uma função personalizada chamada para inicializar as referências para a câmera e o pivô.
- `void FollowTarget(float d)`: É uma função que faz a câmera seguir o jogador.
- `void HandleRotations(float d, float v, float h, float targetSpeed)`: É uma função que lida com as rotações da câmera com base na entrada do mouse.
- `private void FixedUpdate()`: É uma função do Unity chamada antes de cada atualização de física. Aqui, a entrada do mouse é lida e as funções `FollowTarget` e `HandleRotations` são chamadas para mover e girar a câmera, respectivamente.
- `private void LateUpdate()`: É uma função do Unity chamada após todas as funções de atualização terem sido chamadas. Aqui, um raio é lançado da posição do pivô para a posição da câmera para verificar se há algum obstáculo (como uma parede) entre eles. Se houver, a distância da câmera ao pivô é ajustada para evitar que o obstáculo obstrua a visão do jogador.
</p>

<br><br>

<h1> Código de troca de Cena no Unity </h1>
<h3>Quando o jogador encerrar o nível ele precisa encostar em um cubo vermelho, no qual vai levar ele para o próximo nível.</h3>
<br>
<h2>Etapas para Trocar de Cena</h2>
<ul>
 <li>
  Ir em "File" e clicar em "Build Settings";
 </li>
 <li>
   Na janela Build Settings, clique em "Add Open Scenes" para adicionar as cenas que deseja incluir em sua compilação;
 </li>
 <li>
   É recomendável criar um script para lidar com a troca de cena. Você pode fazer isso selecionando "Assets" > "Create" > "C# Script" e dando um nome ao seu script, como "SceneManager" ou algo similar;
 </li>
 <li>
  No script, você pode usar o método `SceneManager.LoadScene` para carregar uma nova cena, como essa que utilizei:
<br>
  
  ```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;

public class LoadGame : MonoBehaviour 
 { 
     public string ProximaFase;
     void OnTriggerEnter(Collider collider)
     {
             // ao colidir no objeto com tag "next" (a tag esta no cubo)
             if(collider.gameObject.tag=="Next")
             {
                     // ir para a segunda fase
                     SceneManager.LoadScene("fase2");
             }
     }
 }
```
 </li>
 <li>
  Certifique-se de que o código acima está em um objeto na cena (por exemplo, um objeto vazio) ou em um objeto relevante para a troca de cena;
 </li>
 <li>
  Certifique-se de que tudo está funcionando corretamente testando o jogo.
 </li>
</ul>

<Br>

## contribuidores

- Mariana Santiago (MariSantiago0)

- Kauã de Castro (KalCastro)

<Br>


<h2>OBS:</h2><h4> O código é feito logicamente por outros programadores, porém reescrito para fins de melhor compreensão.</h4>



