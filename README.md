# SORA-SVL: Local Cloud built for SVL Simulator
---
## About the Project
[LGSVL Simulator](https://github.com/lgsvl/simulator) has been a powerful simulator that made many research projects possible. Unfortunately, LG has made the difficult decision to suspend active development of SVL Simulator, as of January 1, 2022. The official statement says the cloud will be up and running through at least **Thursday, June 30, 2022**.

The current version of SVL Simulator cannot be used without a cloud which provides necessary information (e.g. assetGuid) and download endpoints for SVL client.
As an effort to keep the tool available for future researches, a draft for a local cloud has been started here.

## Built With
1. [Docker](https://www.docker.com/)
2. [NGINX](https://www.nginx.com/) (Router)
3. [MongoDB](https://www.mongodb.com/) (Database)
4. [NodeJS](https://nodejs.org/en/) + [ExpressJS](https://expressjs.com/) (Server)
5. [React](https://reactjs.org/) (Client)


## Getting Started

### Current Version Supports:
1. Viewing maps, vehicles, plugins (previews)
2. Allow SVL Client to connect to a local cloud
3. Start an API Only Simulation

### To Run the Project
1. Install Docker
2. Clone the project
3. Download assets needed from [Google Drive](https://drive.google.com/drive/folders/1bv02d29z4lSB9SWzCBTUt0GjAb876oSR?usp=sharing) and unzip them in `server/assets`
4. Run `docker-compose up --build -d`
5. Local SVL Cloud will be available at "http://localhost"
6. Add `config.yml` to the root directory of SVL client with the following content:
   ```
   headless: false
   read_only: false
   api_hostname: "localhost"
   api_port: 8181
   cloud_url: "http://localhost"
   ```
7. Now, SVL Client can be used without WISE.

## Future Plans
- [ ] Allow creating new simulation templates
- [ ] Allow creating new vehicle sensor configurations
- [ ] Allow website to reflect client connection status
- [ ] Add cluster feature to the cloud

## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request