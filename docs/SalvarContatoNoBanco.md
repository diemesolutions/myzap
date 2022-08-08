Esse tutorial salva o contato que envia uma mensagem para seu número e informa uma caixa para Salvar ou não o contato em nosso banco de dados. 

Ideal para quem quer registrar os contatos efetuados por seus clientes.

Fique atento que esse é o retorno do Webhook quando você recebe uma mensagem:

'wook'      => 'RECEIVE_MESSAGE',
'type'      => 'text',
'id'        => 'false_5527988095543@c.us_3EB0CA',
'session'   => 'nomedasessao',
'isGroupMsg' => false,
'author'    => NULL,
'sender'    => '5527988887777',           //quem está recebendo         
'phone'     => '5527988095543',           //quem está enviando
'content'   => 'Enviado pelo contato',
'status'    => 'RECEIVED',
'timestamp' => 1653331583,

Na versão premium é um pouco diferente - mas é bem intuitivo

"wook"     : "MESSAGE_STATUS",
"status"   : "RECEIVED",
"id"       : "true_5527988095543@c.us_3E3282E",
"session"  : "nomedasessao",
"to"       : "5527988887777",            //quem está recebendo
"from"     : "5527988095543",            //quem está enviando            
"type"     : "text",
"dateTime" : "20-02-2022 08:39:50"

Código dentro da rota WEBHOOK que fará o tratamento da informação recebida.

if(!empty($dados_tratamento['wook'])){                      //existe um retorno de escuta
    if($dados_tratamento['wook'] == 'RECEIVE_MESSAGE'){     //o tipo é de RECEBER MENSAGEM
        if(!empty($dados_tratamento['content'])){           //o content *text* existe
            if($dados_tratamento['content'] <> ''){         //diferente de vazio
                //o que fazer com esse retorno
                
                //verificação do número que entrou em contato
                $numero_que_chamou  = $dados_tratamento['phone'];   //na versão premium é ['from']
                $numero_que_recebeu = $dados_tratamento['sender'];  //na versão premium é ['to']
                
                //se quiser salvar basta executar algum comando referente ao $numero_que_chamou acima
                //tipo esse abaixo:
                \App\Models\Contato::insert([  
                    'phone'     => $numero_que_chamou,  
                    'number'    => $numero_que_chamou,  
                ]);
                
                //com isso podemos trabalhar como quisermos
                //se quiser que envie uma mensagem para o contato bastaria executar o envio por meio de um sendText abaixo
                //processo de envio de mensagem............
                
            }
        }
    }
} 
