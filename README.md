docker
=========

    Install Docker, Docker-Compose, Docker-Logrotate, Cockpit, Cockpit-Docker on Centos 7
    Place template for standalone docker-compose app

Role Variables
--------------

    docker_version:         [default: 3.3] versions of the Compose file format
    docker_service:         [default: service] service name
    docker_image:           [required] docker image name
    docker_restart:         [default: always] no | always | on-failure | unless-stopped 
    docker_hostname:        [default: ansible_fqdn] docker hostname
    docker_ports:           [required] list of mapped ports
    docker_environment:     [not required] list of docker env
    docker_volumes:         [not required] list of mapped volumes
    docker_cap_add:         [not required] list of added container capabilities
    docker_cap_drop:        [not required] list of dropped container capabilities

Example Playbook
----------------

    - hosts: servers
      vars:
        docker_version: 3.3
        docker_service: gitlab
        docker_image: gitlab/gitlab-ce:12.10.13-ce.0
        docker_restart: always
        docker_hostname: git.domain.org
        docker_ports:
          - "8080:80"
          - "8443:443"
          - "8022:22"
        docker_volumes:
          - "./{{ docker_service }}/conf:/etc/gitlab"
          - "./{{ docker_service }}/logs:/var/log/gitlab"
          - "./{{ docker_service }}/data:/var/opt/gitlab"
      roles:
         - docker

License
-------

    MIT

Author Information
------------------

    Dmitrij Petrov
