{% note tip %}
   
Если нет возможности запросить публичный доступ к хостам (например, из соображений безопасности), то Kibana можно воспользоваться, настроив проксирование соединений через виртуальную машину в {{ compute-full-name}} , которая находится в той же [сети](../../vpc/concepts/network.md#network), что и кластер. Подробнее см. в разделе [{#T}](../../managed-elasticsearch/operations/cluster-connect.md).
   
{% endnote %}