# Floresta_Magica
Este e um jogo sobre um percurso onde você tem que levar a esfera pelo percurso, ensinando os tipos de colisores e Triggers.O link do vídeo e do download para o jogo esta no final.<br>
Autores:Kauan Jesus e Ruan Pablo
## Inicio do desenvolvimento
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Primeiro começamos a pensar na ideia do jogo, e resolvemos fazer uma espécie de "Puzzle". Criamos duas cenas no Unity, uma seria o cenário inicial e a outra seria a parte do Puzzle. Para o cenário inicial pegamos varios assets relacionados a floresta (Link dos assets usados no final) e um Asset de uma casa de cogumelo, que serviria como entrada para a cena 2, a cena onde ficaria o Puzzle. Nesta parte, criamos um percurso que estava tampado e era um lugar muito escuro, e junto com você estava uma esfera que brilhava em amarelo. O objetívo do jogo e você levar a esfera pelo percurso ate o final, e no meio do percurso haveria uma porta junto com um pilar, que você tem que descobrir um jeito de passar.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Vale lembrar que depois do primeiro cenario, criamos o personagem, que você seguiria pelo jogo numa visão em 1º pessoa. Vamos chamar este personagem de "Sísifo".
## Os Statics Colliders
![Captura de tela 2023-10-30 075516](https://github.com/KauanJesusJD/Floresta_Magica/assets/127852225/d4a97a66-0c9d-4c56-b127-4c15ee2d1aef)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;No Unity, é possível adicionar "colliders" a objetos que não possuem o componente "rigidbody" para simular pisos e paredes, por exemplo; isso é chamado de Static Collider. A principal diferença deste Collider em relação aos outros é o fato de ser estático. Ele pode interagir com outros Static Colliders e Dynamic Colliders ou Rigidbody Collider, mas não se moverá, pois não possui um rigidbody.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Na imagem a cima e abaixo, utilizamos os Statics Colliders para simular todo o cenário em si, o chão e a parede de arvores, além de utilizarmos uma opcão do Unity que é o "Mesh Collider" que é um static Collider que pega toda a malha do objeto, e tenta fazer uma colisão mais realista, apesar de deixar o jogo mais pesado. Isso vale também para a segunda cena, onde foi utilizado os Static collider para as paredes e o chão.
![Captura de tela 2023-10-30 082023](https://github.com/KauanJesusJD/Floresta_Magica/assets/127852225/3c804ef7-cde4-4d0f-847a-2e358ec73738)
## Os Rigidbody Collider
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Este é o collider que possui um "rigidbody" com a opção "IsKinematic" desativada. Ao contrário dos Static Colliders, eles reagem e se movem quando colidem com outros objetos e são completamente simulados pelo motor de física do Unity. Também respondem a colisões e forças provenientes de um script. Essa é a opção mais comumente usada no Unity, pois pode simular muitos aspectos do mundo dos jogos que envolvem física, como os movimentos de personagens.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;No nosso jogo, utilizamos o rigidbody no personagem (O bloco retangular) e a esfera, para simular o movimento e colisão do personagem.<br>
![Captura de tela 2023-10-30 082556](https://github.com/KauanJesusJD/Floresta_Magica/assets/127852225/7484cdfd-ff22-4fb4-b977-b6a63452b0c9)
## Kinematic Collider
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Este Collider possui um Rigidbody com a opção "IsKinematic" ativada. Eles se comportam de forma semelhante aos Static Colliders, mas podem ser movidos ou ativados ocasionalmente. Por exemplo, uma janela pode se mover (abrindo e fechando) quando necessário, mas permanece estática (fechada).<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Ao contrário dos Static Colliders, um Rigidbody com "IsKinematic" ativado que está se movendo causará fricção em outros objetos e "ativará" outros rigidbodies quando entra em contato com eles. Mesmo quando esse Collider está no modo imóvel, ele age de forma diferente em relação ao Static Collider. Se a colisão serve como um gatilho para alguma ação, você deve adicionar um rigidbody para detectar esse gatilho no script. No entanto, se você não quiser que a colisão seja afetada pela gravidade ou pelas forças da física, você deve ativar o "IsKinematic". Esse tipo de objeto pode ter essa opção ativada e desativada a qualquer momento.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Em termos simples, é como se fosse um Rigidbody Collider que pode se tornar estático a qualquer momento. Um exemplo típico desse collider é o efeito "ragdoll".<br>
![Captura de tela 2023-10-30 083123](https://github.com/KauanJesusJD/Floresta_Magica/assets/127852225/af08d437-2425-49f5-afbf-c9628f2e8ecf)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Utilizamos o Kinematic Collider, para fazer a parede do fundo (Na imagem acima), se mover  para o lado, caso você conseguisse resolver o puzzle. Ela se manteria parada o momento todo, e se moveria caso fosse resolvido o puzzle.
## Trigger Collider
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Antes de passarmos pros próximos colliders, tenho que explicar o que é um Trigger Collider. Ele é uma opção em todos o collider do Unity, a opção “ IsTrigger”, ele pode ser ativado e desativado. Quando ativada, ela não afeta fisicamente o objeto com os quais colide. Ao invés disso, ele é usado principalmente para acionar eventos no script quando outros objetos entram em sua área. Isto pode ser usado para simular vários tipos de interações, como abrir uma caixa e coletar itens.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Normalmente se utiliza a função “OnCollisionEnter”, porém, pode se usar o motor de física do Unity para detectar quando um collider entra no espaço do outro sem criar uma colisão.<br>
Um Collider com a opção “IsTrigger” ativada não vai agir como um objeto sólido, e vai simplesmente deixar outros colliders passarem por ele.
## Static Trigger Collider e OnTriggerEnter
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Um tipo específico de Trigger Collider para objetos estáticos. Este tipo de Collider é usado para detectar quando algo entra em sua área sem causar movimento ou colisões físicas. Isso é útil para criar áreas de detecção em cenários ou objetos que não mudam de posição.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Assim como os Static Colliders, este Trigger Collider diferente dos outros, e um Trigger que sempre se mantém estático, para detecção de colisão para objetos estáticos, sem nenhum tipo de reação física. Porém, diferentemente do Static Collider, quando algum outro Collider entra na área do Static Trigger Collider ele ativa algum tipo de evento (Como dito anteriormente).<br>
![image](https://github.com/KauanJesusJD/Floresta_Magica/assets/127852225/690ac8fb-c25e-4d34-9a7c-e3df6bdc9769)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;No jogo, utilizamos isso nessa casa de cogumelos, para que a partir do momento, que o colisor do personagem entrasse no colisor dessa casa, o personagem iria entrar na segunda cena. Como é possivel ver, o Istrigger desse collider está ativado. Nos fizemos isso com base no codígo abaixo, utilizando o comando "OnTriggerEnter" e colocando a tag no nosso personagem de "Player" e partir do momento que acontecesse a colisão o "SceneManager" iria abrir a cena "Puzzles_Cena".

      using System.Collections;
      using System.Collections.Generic;
      using UnityEngine;
      using UnityEngine.SceneManagement;
      
      public class EntrarCasa : MonoBehaviour
      {
          // Muda de cena quando o player entra no trigger da casa
          void OnTriggerEnter(Collider other){
              if(other.gameObject.CompareTag("Player")){
                  SceneManager.LoadScene("Puzzles_cena");
              }
          }
      }

## Rigidbody Trigger Collider
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Assim como o Rigidbody Collider, este sofre algum tipo de reação quando entra em contato com outro Collider. Porém, diferentemente do Rigidbody Collider, quando o Rigidbody Trigger Collider colide com outro Collider, ele não causa forças físicas ao outro objeto e o Rigidbody Collider causa. Utilizamos este no pilar que serve para ativar a porta. há um codígo relacionado a este objeto também, mas iremos falar dele no ultimo tipo de Collider e trigger.
## Kinematic Trigger Collider e OnTriggerStay
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Funciona da mesma forma que o Kinematic Rigidbody Collider, porém tem a funcionalidade do Trigger Collider ativada. As diferenças deste Trigger Collider para os outros são iguais as do Kinematic Rigidbody Collider, porém, a diferença deste para o Kinematic Rigidbody Collider e que este não aplica forças físicas a outros objetos e não os movem, somente servindo como detecção para algum outro collider (ativando algum tipo de evento).<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;No nosso jogo utilizamos este para abrir a porta do meio do percurso da cena 2, utilizando o codígo abaixo. No codígo abaixo, criamos um timer de 5 segundos que a esfera teria que ficar no pilar, para que a porta abrisse, mas este contador so iria iniciar se a esfera estivesse no pilar, iniciando com o valor "false" e virando "true" quando a esfera estivesse no pilar. Também colocamos uma tag na esfera de "esfera", para que esta reconhecesse a colisão da esfera no pilar.Nos conectamos este codígo com a parede e utilizamos o "OnTriggerStay" para que a contagem so ativasse quando o "gatilho" continuasse sendo constantemente ativado, e quando desse 5 segundos disso, a porta se moveria para o lado (Usando translate e vetor). Também utilizamos o "OnTriggerExit" para que quando a esfera saisse do pilar, a contagem voltaria a 0 e a parede pararia de se mexer.

    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;
    
    public class AbrirPorta : MonoBehaviour
    {
        private bool iniciarContador = false;
        private float contador = 0f;
        public GameObject parede;
        // Start is called before the first frame update
        void Start()
        {
    
        }
    
        // Update is called once per frame
        void Update()
        {
            if(iniciarContador == true){
                contador += 1 * Time.deltaTime;
                if(contador > 5){
                    parede.transform.Translate(Vector3.back * 2f * Time.deltaTime);
                }
            }
        }
    
        void OnTriggerStay(Collider other){
            if(other.gameObject.CompareTag("esfera")){
                iniciarContador = true;
            }
        }
    
        void OnTriggerExit(Collider other){
            if(other.gameObject.CompareTag("esfera")){
                iniciarContador = false;
                contador = 0f;
            }
        }
    }
## OnTriggerExit
![image](https://github.com/KauanJesusJD/Floresta_Magica/assets/127852225/0c42669b-498d-4ea4-b7a9-e59bbceb84f2)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Nos também utilizamos o "OnTriggerExit" (como no codígo abaixo) para que quando a tag "esfera" (do objeto esfera) saisse do colisor do percurso, ele mostraria o texto "Você completou o percurso", ja que o texto estava "false". Para isso criamos um Canvas no Unity, como o normal.<br>
![Captura de tela 2023-10-30 113846](https://github.com/KauanJesusJD/Floresta_Magica/assets/127852225/12c6ed9a-b570-4e7d-9ebc-3840c40e1e30)

    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.UI;
    
    public class SairPercurso : MonoBehaviour
    {
        public Text texto;
        // Start is called before the first frame update
        void Start(){
            texto.enabled = false;
        }
    
        void OnTriggerExit(Collider other){
            if(other.gameObject.CompareTag("esfera")){
                texto.enabled = true;
            }
        }
    }

## Movimentação
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Na movimentação, nos criamos primeiro uma variavel para a velocidade de movimento e a velocidade de rotação da camera. Com base no codígo abaixo.

    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;
    
    public class Movimentação : MonoBehaviour
    {
    	public float speed = 10.0f;
    	public float rotationSpeed = 2f;
    	private Vector3 direcao;
        // Start is called before the first frame update
        void Start()
        {
    
        }
    
        // Update is called once per frame
        void Update()
    
        {
    		float moverH = Input.GetAxis("Horizontal");
    		float moverV = Input.GetAxis("Vertical");
    
    		direcao = new Vector3(moverH, 0, moverV) * speed * Time.deltaTime;
    		transform.Translate(direcao);
    
    		float mouseXInput = Input.GetAxis("Mouse X");
    
            // Rotacionar o personagem em torno do eixo Y
            transform.Rotate(0f, mouseXInput * rotationSpeed, 0f);
    	}
    }
# Link dos Assets utilizados
https://assetstore.unity.com/packages/3d/vegetation/trees/free-trees-103208<br>
https://assetstore.unity.com/packages/2d/textures-materials/nature/terrain-textures-pack-free-139542<br>
https://assetstore.unity.com/packages/3d/environments/fantasy/mushroom-house-61027<br>

# Link do jogo e o vídeo🌲🍄 (Compactado)
https://drive.google.com/drive/folders/1HWXEmf0onWxrHDEeAVHlsJB1O9jh1myP?usp=drive_link



