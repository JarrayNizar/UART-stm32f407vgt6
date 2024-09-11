# UART-stm32f407vgt6
Le projet transfère la chaîne de caractères "nizar" entre les cartes en utilisant les modes interruption et DMA pour la gestion des données.

Modes Utilisés :

# Mode Interruption :

Transmission : Les LED orange et bleue clignotent pendant l'envoi des données. Une fois la transmission terminée, la LED verte s'allume, contrôlée par le HAL_UART_TxCpltCallback.
Réception : Sur la carte réceptrice, les LED orange et bleue clignotent pendant la réception, et la LED verte confirme la réception des données via le HAL_UART_RxCpltCallback. En cas d’erreur, la LED rouge s’allume.
# Mode DMA :

Transmission : Les données du TX_Buffer sont automatiquement transférées au UART_TX_DR en utilisant le DMA. La LED verte indique une transmission réussie, tandis qu'en cas d’erreur, la LED rouge s'allume.
Réception : Le DMA transfère les données du UART_RX_DR vers la mémoire. Une fois la réception terminée, la LED verte s'allume et les erreurs sont indiquées par la LED rouge.
Périphériques Utilisés :

UART : Gère la communication asynchrone des données.
RCC : Configure les signaux d’horloge pour une opération stable.
NVIC : Gère les interruptions pour un traitement efficace.
GPIO : Contrôle les LED pour fournir un retour visuel sur l’état des opérations.
Importance des Callbacks :

HAL_UART_TxCpltCallback : Ce callback est déclenché lorsque la transmission UART est terminée. Il est essentiel pour que le système sache que les données ont été entièrement transmises, permettant ainsi à la LED verte de s'allumer comme confirmation. Cela garantit la synchronisation du système et évite les pertes de données.
HAL_UART_RxCpltCallback : Ce callback est appelé lorsque des données sont reçues. Il est crucial pour vérifier l'exactitude des données reçues et déclenche la LED verte en cas de réception réussie. En cas d'échec, il active la LED rouge, aidant ainsi à la détection et à la correction des erreurs.
Présentation du Projet :
