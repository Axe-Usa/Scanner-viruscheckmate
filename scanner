<?php
 
 
function viruscheckmate ($domain) {
    $vcm_server = "http://viruscheckmate.com/api/v1/check/new/";
    $vcm_apikey = "API_KEY"; // <--- is taken in the settings from the IP from which the script runs
    $params = array (
                    'apikey' => $vcm_apikey,
                    'url' => $domain,
                    // 'use_profile' => 'chdomain', <- - uncomment when the
                    'task_type' => 'domain'
                    );
    $ch = curl_init ();
    curl_setopt ($ch, CURLOPT_URL, $vcm_server);
    curl_setopt ($ch, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt ($ch, CURLOPT_POST, 1);
    $result = curl_exec ($ch);
 
    $response = json_decode ($result, true);
    $detect = 0;
    if ($response ['status'] == 1) {
        $d = $response ['data'];
        foreach ($d ['results'] as $engine => $objects) {          
            foreach ($objects ['objects'] as $object => $result) {
                if ($result ['fast_detect'] == 1) {            
                    $detect ++;
                }
            }
        }
    }
    return $detect;
}
 
echo viruscheckmate ("www.ya.ru");
 
?>
