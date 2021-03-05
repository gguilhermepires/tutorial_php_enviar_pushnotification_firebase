# tutorial_php_enviar_pushnotification_firebase

Pegar o token do firebase na configuração do projeto/Cloud Messaging
Pegar o token do celular forcecido pelo app

## enviar mensagem
        $TokenFirebasekey ='A..';
        $tokenCelular = 'c3...e';
        
        $data = array("to" => $tokenCelular, "notification" => array(
        "title" => "tutorialGuilherme.com", "body" => 
        "guilherme!","icon" => "icon.png", "click_action" => "https://github.com/gguilhermepires/tutorial_php_enviar_pushnotification_firebase/edit/main/README.md"));
        $data_string = json_encode($data);
        
        echo "The Json Data : ".$data_string;
        
        $headers = array ( 'Authorization: key=' . $TokenFirebasekey, 'Content-Type: application/json' );
        $ch = curl_init(); curl_setopt( $ch,CURLOPT_URL, 'https://fcm.googleapis.com/fcm/send' );
        curl_setopt( $ch,CURLOPT_POST, true );
        curl_setopt( $ch,CURLOPT_HTTPHEADER, $headers );
        curl_setopt( $ch,CURLOPT_RETURNTRANSFER, true );
        curl_setopt( $ch,CURLOPT_POSTFIELDS, $data_string);
        $result = curl_exec($ch);
        curl_close ($ch);
        
        echo "<p>&nbsp;</p>";
        echo "The Result : ".$result;
