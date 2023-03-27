################################## SELF HOSTED RUNNER #################################################################

- How install selF hosted  : https://www.youtube.com/watch?v=SASoUr9X0QA

- About self hosted : https://docs.github.com/en/actions/hosting-your-own-runners

- About self hosted : https://docs.github.com/en/actions/hosting-your-own-runners/monitoring-and-troubleshooting-self-hosted-runners

- Runner service
  sudo ./svc.sh install
  sudo ./svc.sh start
  sudo ./svc.sh status
  sudo ./svc.sh stop

- Get logs from de runner service after installation
  sudo journalctl -u actions.runner.CHONG-TECHNOLOGIES.rn-ansible-env.service --follow



  ################################### TRIGGER WORKFLOW ##############################################################

  - https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows