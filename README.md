<p align="center">
	<a href="https://github.com/Gingmzmzx/AKIOIOJ">
		<img src="https://rawgit.com/Gingmzmzx/AKIOIOJ/master/.github_banner.png" alt="vj4" width="100%" align="middle" />
	</a>
</p>

<p align="center">
	Docker version of <a href="https://github.com/Gingmzmzx/AKIOIOJ">AKIOIOJ</a>, the next generation of <a href="https://oj.xzynb.top" target="_blank">Online Judge</a>.
</p>

<p align="center">
	Adapt from <a href="https://github.com/vijos/vj4-docker">Vijos/vj4-docker</a>
</p>

<p align="center">
	<small><a href="./README.zh-CN.md">中文</a></small>
</p>

***

## Quick Start

Start your own AKIOIOJ with Docker in minutes!

```bash
git clone https://github.com/Gingmzmzx/akioioj-docker.git
cd akioioj-docker
cp .env.example .env
docker-compose up -d
```

Wait for seconds for services to be up and running, then you can access your own AKIOIOJ with `http://<ip>:8888`.

To add a super administrator:

```bash
alias drpm="docker-compose run --rm web"
drpm vj4.model.user add -1 soha 233333 soha@lohu.info # uid username password email
drpm vj4.model.user set_superadmin -1 # uid
```

## Judging

To enable judging, you should configure a judge account first:

```bash
alias drpm="docker-compose run --rm web"
drpm vj4.model.user add -2 judge 123456 judge@example.org # uid username password email
drpm vj4.model.user set_judge -2 # uid
```

Then download a example judge configuration file:

```bash
mkdir -p ./data/judge/ && wget -O ./data/judge/config.yaml https://raw.githubusercontent.com/Gingmzmzx/jd4/master/examples/config.yaml
# fill account info of judge user you've created before in config.yaml 
nano ./data/judge/config.yaml
```

You can use `http://web:8888/` as `server_url` in `config.yaml` if the web service is listening to port in the container.

Edit `docker-compose.yml` and uncomment `judge` block and `docker-compose down && docker-compose up -d`.

Now your can judge your codes on your AKIOIOJ!
