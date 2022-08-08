
Retornos para mensagens

​Os retornos de envios e recebimentos de mensagens seguem algumas semelhanças entre o Free e o Premium.

Para o free temos:

Ao enviar mensagens - exemplo​

{
    'wook'       => 'MESSAGE_STATUS',     
    'status'     => 'SENT',     
    'id'         => 'true_5527988095543@c.us_B0204010AF',     
    'session'    => 'session',    
    'phone'      => '5527988095543',     
    'content'    => 'Mensagem de saída',     
    'timestamp'  => 1653331491,     
    'type'       => 'text',
}

Ao receber mensagem - exemplo​

{
​   'wook'       => 'RECEIVE_MESSAGE',
    'type'       => 'text',
    'id'         => 'false_5527988095543@c.us_3EB08BCEFEA6647F4B19',
    'session'    => 'SessaoComWebhook',
    'isGroupMsg' => false,
    'author'     => NULL,
    'sender'     => '552799998888',    //em sender fica o número que está conectado na sessão
    'phone'      => '5527988095543',
    'content'    => 'Mensagem recebida',
    'status'     => 'RECEIVED',
    'timestamp'  => 1653594703,
}

Se a mensagem foi entregue ao destinatário ele marca como RECEIVED em STATUS.

Na versão premium temos:

Ao enviar mensagem - exemplo​

{
    "wook"         : "SEND_MESSAGE",
    "type"         : "text",            //image, sticker, audio, video
    "fromMe"       : true,
    "id"           : "true_5527988887777@c.us_3EB0E070AEA867AA0DC5",
    "session"      : "session",
    "isGroupMsg"   : false,
    "author"       : null,
    "name"         : "nome do contato",
    "to"           : "5527988887777",
    "from"         : "5527988095543",
    "content"      : "mensagem",
    "quotedMsg"    : "",             //se a mensagem tivesse sido marcada
    "quotedMsgId"  : "",             //id da mensagem marcada    
    "status"       : "SENT",
    "datetime"     : "26-05-2022 05:00:03"
}​

Ao receber mensagem

Mensagem lida pelo destinatário - exemplo​

{
​    "wook"        : "MESSAGE_STATUS",
​    "status"      : "READ",
​    "id"          : "true_5527988095543@c.us_2CE809D0084A9",
​    "session"     : "session​",
​    "to"          : "5527988095543​",
​    "from"        : "5527999998888",
​    "type"        : "text",
​    "dateTime"    : "26-05-2022 09:55:02"
​}​​

Mensagem recebida  - exemplo

{
​    "wook"        : "RECEIVE_MESSAGE",
​    "type"        : "text",
​    "fromMe"      : false,
​    "id"          : "false_100000000000050@g.us_38728400298@c.us",
​    "session"     : "session",
​    "isGroupMsg"  : true,        //veio de grupo        
​    "author"      : "55279999988888@c.us",
​    "name"        : "Nome do contato",
​    "to"          : "5527988095543",
​    "from"        : "100000000000050​",
​    "content"     : "Mensagem",
​    "quotedMsg"   : "",
​    "quotedMsgId" : "",
    "status"      : "RECEIVED",
​    "datetime"    : "26-05-2022 09:54:30"
​}​

Acima alguns exemplos de webhooks das mensagens. Trabalhe nelas na rota Webhook.
