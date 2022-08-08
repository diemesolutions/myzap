Dicas de uso no Firebase

Todo problema de conexão - seja de acesso ao banco, problemas de salvar a sessão no firebase podem ser relacionados a:

Regra de permissão estar como TRUE ​como descrito abaixo.

rules_version = '2';
service cloud.firestore {  
    match /databases/{database}/documents {    
        match /{document=**} {      
            allow read, write: if true;    
        }  
    }
}

    Você pode também criar uma COLLECTION chamada sessions no seu firebase para "forçar o início das sessões";
    Reiniciar sua API Myzap através do pm2 restart x (número id da aplicação myzap no PM2);

Outras opções serão sendo acrescentadas aqui.
