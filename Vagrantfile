Vagrant.configure("2") do |config|
  
  # Introduce aquí la configuración del servidor virtual
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "private_network", ip: "192.168.49.49"
  config.vm.synced_folder ".", "/trabajo_tema7_SISIN"

  config.vm.provision "shell", inline: <<-SHELL
      # Instalación de los binarios de PHP, el driver mysqli y la extensión FPM para realizar peticiones de tipo RESTful
    sudo apt update
    sudo apt install -y nginx
    sudo apt install -y php php-mysqli
    sudo sed -i -e 's/\\/var\\/www\\/html/\\/trabajo_tema7_SISIN/g' /etc/nginx/sites-enabled/default
      # Generar archivo SQL con los registros de los diferentes Módulos Profesionales
    echo "-- Insertar datos de ejemplo en la tabla 'horario'" > /home/vagrant/trabajo_final.sql
    echo "INSERT INTO gestion_modulos_profesionales.horario (lunes, martes, miercoles, jueves, viernes) VALUES" >> /home/vagrant/trabajo_final.sql
    echo "('ENDES', 'ENDES', 'LMSGI', 'FOL', 'PROGR')," >> /home/vagrant/trabajo_final.sql
    echo "('LMSGI', 'ENDES', 'LMSGI', 'SISIN', 'BADAT')," >> /home/vagrant/trabajo_final.sql
    echo "('LMSGI', 'SISIN', 'BADAT', 'SISIN', 'BADAT')," >> /home/vagrant/trabajo_final.sql
    echo "('PROGR', 'FOL', 'SISIN', 'PROGR', 'LEUP')," >> /home/vagrant/trabajo_final.sql
    echo "('PROGR', 'PROGR', 'SISIN', 'BADAT', 'LEUP')," >> /home/vagrant/trabajo_final.sql
    echo "('BADAT', 'PROGR', 'PROGR', 'BADAT', 'FOL')" >> /home/vagrant/trabajo_final.sql

  SHELL

end
