# SSH Port Forwarding (SSH Tunneling)
- 보안 때문에 서버의 포트를 오직 SSH만, 또는 서비스를 위한 특정 포트만 열어둔 경우가 많다. 한편 서버 관리를 위해 개방되지 않은 포트에 접근해야할 필요성이 있는데 이 때 SSH Port Forwarding을 통해 해결할 수 있다. 
- SSH Port Forwarding (SSH Tunneling) : SSH 프로토콜을 이용하여 직접 접속할 수 없는 Port와 연결통로(터널)을 만들어 접근할 수 있도록 하는 기술 
- SSH Port Forwarding에는 아래 3가지 종류가 있다. 
  - Local Port Forwarding : Local에서 Remote 특정 Port에 접근하고자 하는 경우
  - Remote Port Forwarding : Remote에서 Local 특정 Port에 접근을 허용하고자 하는 경우 (써보지 않음)
  - Dynamic Port Forwarding (써보지 않음)
- Local Port Forwarding 예시
```bash
ssh -L <Local에서 사용할 port>:<최종적으로 접근할 IP>:<최종적으로 접근할 Port> <SSH 서버 계정>@<SSH 서버 IP>

# ubuntu 계정 111.111.111.111 IP 서버의 Docker bridge network ip가 127.0.0.1 이며, 여기에 5000 포트로 뜬 도커 컨테이너 서비스에 접근하고 싶은 경우 (로컬에서도 5000포트로 접근)
ssh -L 5000:127.0.0.1:5000 ubuntu@111.111.111.111
```
- 참고 : https://unix.stackexchange.com/questions/115897/whats-ssh-port-forwarding-and-whats-the-difference-between-ssh-local-and-remot