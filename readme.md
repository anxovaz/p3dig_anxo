<h1>Practica DIG - Anxo Vázquez Lorenzo</h1>

<h2>1. Realiza unha consulta "dig danielcastelao.org"</h2>
<p>Identifica cada parte da resposta (IN, CNAME, A, QUERY SECTION, ANSWER SECTION, AUTHORITY SECTION, etc).</p>
<p>Para realizar unha consulta con dig usase "dig danielcastelao.org".</p>
<p>dig danielcastelao.org</p>

<h2>2. Realiza consultas dos seguintes nomes e identifica as diferencias</h2>
<p>moodle.danielcastelao.org, www.danielcastelao.org.</p>
<p>Cando executase dig sobre moodle.danielcastelao.com a sección de ANSWER mostra 2 servidores de aws, outra das cousas que cambia é o tamaño de mesaxe recibido de 54 de moodle.danielcastelao.com a 63 de danielcastelao.org.</p>
<p>dig danielcastelao.org</p>
<p>dig moodle.danielcastelao.com</p>

<h2>3. Averigua o nome e IP dos servidores de DNS autoritativos de www.danielcastelao.org</h2>
<p>Por qué soen ser 2 servidores autoritativos?</p>
<p>danielcastelao.org → 178.211.133.37</p>
<p>moodle.danielcastelao.com → 18.119.154.66 e 3.140.13.188</p>

<h2>4. Realiza as consultas de nomes inversas</h2>
<p>130.206.164.68 e de outras dúas IPs que se che ocorran.</p>
<p>dig -x 130.206.164.68</p>
<p>dig -x 8.8.8.8</p>
<p>dig -x 8.8.4.4</p>

<h2>5. A qué servidor DNS estás consultando?</h2>
<p>Cómo o podes cambiar sen tocar os ficheiros de configuración do sistema?</p>
<p>Cando executo o comando dig exemplo.com móstrase ao final de todo o servidor DNS ao que se está realizando a consulta, no meu caso 127.0.0.53.</p>
<p>dig google.es</p>

<h2>6. Obtén o rexistro SOA (Start of Authority)</h2>
<p>Do dominio moodle.danielcastelao.org preguntándolle ó servidor DNS de google e logo preguntándollo directamente ó servidor primario do dominio danielcastelao.org.</p>
<p>Para saber o rexistro SOA añado a palabra SOA ao final do comando, e para preguntarlle ao servidor DNS de google ou o de danielcastelao.org o indico co "@"</p>
<p>dig @8.8.8.8 moodle.danielcastelao.com SOA</p>
<p>dig @178.211.133.37 moodle.danielcastelao.com SOA</p>

<h2>7. Consulta a IP de www.elpais.com</h2>
<p>Cánto tempo queda almaceado o rexistro de recurso no DNS local? Se preguntas ó DNS local por este recurso, qué observas no TTL do rexistro?</p>
<p>Ao realizar o dig sobre elpais.com na sección de answer mostra o TTL da consulta, neste caso 178.</p>
<p>dig www.elpais.com</p>

<h2>8. Busca o TTL de distintos nomes de dominio de servicios que escollas</h2>
<p>A qué se poden deber as diferencias?</p>
<p>Depende de cantos saltos tenga que dar a mensaxe ata chegar ao emisor (servidor).</p>
<p>dig google.es</p>
<p>dig elpais.com</p>

<h2>9. Determina o TTL máximo (original) dun nome de dominio</h2>
<p>604800 segundos (1 semana)</p>

<h2>10. Averigua cántas máquinas con distintas IPs están detrás do dominio web www.google.es</h2>
<p>Sempre son as mesmas e na mesma orde? Por qué?</p>
<p>Usando "dig dominio.com +short" podo ver as direccións IP que ten un dominio, non teñen porque ser sempre as mesmas, xa que facendo o dig sobre www.google.es dá a saída de 142.250.184.163 mentres que se o fago sobre dominio.com dame a saída de 142.250.184.164.</p>
<p>dig www.google.es +short</p>

<h2>11. Pregunta o mesmo a un server raíz</h2>
<p>(J.ROOTSERVERS.NET por exemplo) e comproba na resposta se o server acepta o modo recursivo.</p>
<p>Ao facer o dig sobre J.ROOTSERVERS.NET dá 2 direccións IP (3.33.243.145 e 15.197.204.56), o server acepta modo recursivo porque no header mostra o parámetro "ra": flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1.</p>
<p>dig J.ROOTSERVERS.NET</p>

<h2>12. Se queremos ver todas as queries que fai o servidor de DNS</h2>
<p>Qué opción temos que usar? Averigua a IP de www.timesonline.co.uk, especifica os pasos dados.</p>
<p>Para averiguar a IP de www.timesonline.co.uk uso o comando "dig dominio.com", o cal mostra as seguintes IPs: 54.76.240.177, 34.240.28.43 e 52.208.17.106.</p>
<p>dig www.timesonline.co.uk</p>

<h2>13. Usando a información dispoñible a través do DNS</h2>
<p>Especifica a máquina (nome e IP) ou máquinas que actúan como servers de correo do dominio danielcastelao.org.</p>
<p>Usando MX ao final do comando dig mostra todos os servidores de correo dun dominio.</p>
<p>ANSWER SECTION:</p>
<p>danielcastelao.org. 900 IN MX 100 alt2.aspmx.l.google.com.</p>
<p>danielcastelao.org. 900 IN MX 80 aspmx.l.google.com.</p>
<p>danielcastelao.org. 900 IN MX 110 aspmx2.googlemail.com.</p>
<p>danielcastelao.org. 900 IN MX 120 aspmx3.googlemail.com.</p>
<p>danielcastelao.org. 900 IN MX 130 aspmx4.googlemail.com.</p>
<p>danielcastelao.org. 900 IN MX 140 aspmx5.googlemail.com.</p>
<p>danielcastelao.org. 900 IN MX 90 alt1.aspmx.l.google.com.</p>
<p>dig danielcastelao.org MX</p>

<h2>14. Podes obter os rexistros AAAA de www.facebook.com?</h2>
<p>A qué corresponden?</p>
<p>Escribindo AAAA ao final do comando mostra os seguintes rexistros:</p>
<p>www.facebook.com. 210 IN CNAME star-mini.c10r.facebook.com.</p>
<p>star-mini.c10r.facebook.com. 15 IN AAAA 2a03:2880:f104:83:face:b00c:0:25de</p>
<p>dig www.facebook.com AAAA</p>
