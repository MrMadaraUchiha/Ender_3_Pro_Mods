# Usuários de Windows: Para editar este arquivo, utilize Notepad++, VSCode, Atom ou SublimeText.
# Não utilize Notepad ou WordPad.

# Usuários de MacOSX: Se você usar o Textedit para editar este arquivo, certifique-se de usar
# o "formato de texto simples" e "desativar aspas inteligentes" em "Textedit > Preferências".

# Configuração de qual câmera usar
# 
# Opções disponíveis são:
# - auto: tenta primeiro a webcam USB; se não estiver disponível, tenta a câmera Raspi
# - usb: tenta apenas a webcam USB
# - raspi: tenta apenas a câmera Raspi
# 
# O padrão é auto.
# 
camera: "auto"

# Opções adicionais para fornecer ao MJPG Streamer para a câmera USB
# 
# Veja https://faq.octoprint.org/mjpg-streamer-config para opções disponíveis.
# 
# O padrão é uma resolução de 640x480 px e uma taxa de quadros de 10 fps.
# 
camera_usb_options: "-r 1280x720 -f 25"

# Dispositivos de webcam adicionais conhecidos por causarem problemas com -f
# 
# Aparentemente, existem alguns dispositivos que, com a versão atual
# do mjpg_streamer, não suportam o parâmetro -f (para especificar a
# taxa de quadros de captura) e se recusam a produzir uma imagem se ele
# for fornecido.
# 
# O daemon da webcam detectará esses dispositivos por meio do ID do
# fornecedor e produto USB e removerá o parâmetro -f das opções fornecidas
# ao mjpg_streamer.
# 
# Por padrão, isso é feito para os seguintes dispositivos:
#   Logitech C170 (046d:082b)
#   GEMBIRD (1908:2310)
#   Genius F100 (0458:708c)
#   Cubeternet GL-UPC822 UVC WebCam (1e4e:0102)
# 
# Usando a opção abaixo, é possível adicionar dispositivos adicionais. Se
# sua webcam apresentar os sintomas acima, tente determinar o ID do fornecedor
# e produto da sua câmera via lsusb, ativando a linha abaixo removendo o # e
# adicionando os IDs, por exemplo, para duas câmeras com problemas "aabb:ccdd" e "aabb:eeff".
# 
#   additional_brokenfps_usb_devices: ["aabb:ccdd", "aabb:eeff"]
# 
additional_brokenfps_usb_devices: []

# Opções adicionais para fornecer ao MJPG Streamer para a câmera RasPi
# 
# Veja https://faq.octoprint.org/mjpg-streamer-config para opções disponíveis.
# 
# O padrão é 10fps.
# 
camera_raspi_options: "-fps 10"

# Configuração de saída HTTP da câmera
# 
# Normalmente, você NÃO deve precisar alterar isso! Alterar somente se você
# souber o que está fazendo e o que os parâmetros significam.
# 
# As configurações abaixo são usadas na chamada do mjpg-streamer assim:
# 
#   -o "output_http.so -w $camera_http_webroot $camera_http_options"
# 
# O diretório de trabalho atual é o diretório base do mjpg-streamer.
# 
camera_http_webroot: "./www-mainsail"
camera_http_options: "-n"

# EXPERIMENTAL
# Suporte para diferentes tipos de streamer.
# 
# Opções disponíveis:
#   mjpeg [padrão] - MJPG-streamer estável
camera_streamer: mjpeg
