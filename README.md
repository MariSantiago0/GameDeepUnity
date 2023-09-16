# GameDeepUnity

<h1>Códigos do Jogador</h1>
<h2> Movimentação</h2>
<p>
<strong>Este é um script de controle do jogador para um jogo em 3D usando o motor Unity. Aqui está uma explicação básica de algumas partes do código:</strong>

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

O método `Start()` é chamado no início do jogo. Ele obtém a distância até o chão.<br>
O método `IsGrounded()` verifica se o personagem está no chão.<br>
O método `Awake()` é chamado quando o script é carregado. Ele obtém o componente Rigidbody do personagem e desativa a rotação e a gravidade automáticas.<br>
O método `FixedUpdate()` é chamado a cada quadro fixo (frame). Ele controla o movimento e a rotação do personagem, aplica a força da gravidade e permite ao personagem pular.<br>
O método `Update()` é chamado uma vez por quadro (frame). Ele obtém os inputs do usuário para mover o personagem.<br>
</p>

<h2>Perder vida ao colidir</h2>
<p>
 <strong>Este é um script de controle de vida do jogador caso o jogador colida com um obstáculo. Aqui está uma explicação básica de algumas partes do código:</strong> 

- `public int vidas = 3;` : Este é o número inicial de vidas do personagem.
- `void OnCollisionEnter(Collision collision)` : Este método é chamado quando o personagem colide com outro objeto. O objeto com o qual o personagem colidiu é passado como um parâmetro.
- `if (collision.gameObject.CompareTag("obstaculos"))` : Esta linha verifica se o objeto com o qual o personagem colidiu tem a tag "obstaculos". Se tiver, o código dentro das chaves `{}` será executado.
- `vidas--;` : Esta linha diminui o número de vidas do personagem em 1.
- `Debug.Log("Vida perdida! Vidas restantes: " + vidas);` : Esta linha imprime uma mensagem no console do Unity informando que uma vida foi perdida e quantas vidas restam.
- `if (vidas <= 0)` : Esta linha verifica se o número de vidas do personagem é menor ou igual a zero. Se for, o código dentro das chaves `{}` será executado.
- `Debug.Log("Game Over!");` : Esta linha imprime uma mensagem no console do Unity informando que o jogo acabou.
- `#if UNITY_EDITOR UnityEditor.EditorApplication.isPlaying = false; #else Application.Quit(); #endif` : Este bloco de código termina o jogo. Se o jogo estiver sendo executado no editor Unity, ele irá parar a reprodução. Se o jogo estiver sendo executado fora do editor, ele irá fechar a aplicação.
</p>

<h1>Código dos Obstáculos</h1>
<h2>Código da Parede móvel (WallMoveable)</h2>
<p>
  
- `public bool isDown = true;` : Esta variável determina se a parede começa em uma posição baixa. Se a parede não começar em uma posição baixa, você deve modificar para false.
- `public bool isRandom = true;` : Esta variável determina se a parede deve se mover para cima e para baixo de maneira aleatória.
- `public float speed = 2f;` : Esta é a velocidade com que a parede se move.

- `void Awake()` : Este método é chamado quando o script é carregado. Ele obtém a altura da parede e a posição inicial da parede.
- `void Update()` : Este método é chamado uma vez por quadro (frame). Ele controla o movimento da parede. Se a parede estiver em uma posição baixa, ela se moverá para cima. Se a parede estiver em uma posição alta, ela se moverá para baixo.
- `IEnumerator WaitToChange(float time)` : Esta função faz com que a parede espere por um certo tempo antes de mudar de direção. Se a variável `isRandom` for verdadeira e a parede estiver em uma posição alta, a função pode decidir aleatoriamente se a parede deve começar a se mover para baixo ou não.
- `IEnumerator Retry(float time)` : Esta função verifica periodicamente se a parede pode começar a se mover para baixo. A verificação ocorre a cada 1,25 segundos.
</p>

<h2>Código do Obstáculo móvel </h2>
<p>
  
- `public class MovableObs : MonoBehaviour`: Esta linha define uma nova classe chamada `MovableObs` que herda de `MonoBehaviour`, que é a classe base de onde todos os scripts Unity derivam.
- `public float distance = 5f;`: Define a distância que o objeto se move.
- `public bool horizontal = true;`: Define se o movimento é horizontal ou vertical.
- `public float speed = 3f;`: Define a velocidade do movimento do objeto.
- `public float offset = 0f;`: Permite modificar a posição inicial do objeto.
- `private bool isForward = true;`: Define se o movimento é para fora.
- `private Vector3 startPos;`: Armazena a posição inicial do objeto.
- `void Awake()`: É uma função do Unity chamada quando o script é carregado. Aqui, a posição inicial do objeto é armazenada e o deslocamento é aplicado à posição inicial.
- `void Update()`: É uma função do Unity chamada uma vez por frame. Aqui, o objeto é movido para frente e para trás ao longo do eixo x (se `horizontal` for verdadeiro) ou z (se `horizontal` for falso) entre sua posição inicial e sua posição inicial mais a distância definida.
</p>
