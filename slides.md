---
theme: default
background: /background.jpg
title: Secure by Design
drawings:
  persist: false
transition: none
mdc: true
shiki: { theme: "nord" }
---

# Secure by Design

## How Hardened Images Make Your Java Services Bullet-Proof

Catherine Edelveis, BellSoft

---

# whoami

- Developer Advocate at BellSoft
- Focused on the JVM ecosystem
- Tech writer
- CyberJAR YouTube channel co-host
- Unorthodox by design

---

# whoarewe to talk about security?

- Members of OpenJDK Vulnerability Group
- Commit fixes and patches upstream
- In-house JDK and Linux patching
- <span v-mark.box.purple="1"> Hardened container images </span>

<v-click>

...wait, what?

</v-click>

---
layout: cover
---

## What are hardened container images?

---
layout: cover
---

## Let's take a few steps back. We can't start the story from the middle, right?

---
layout: image
image: /old-city.png
---

---
layout: image
image: /old-city.png
---

## The container image should be a safe city for your app, yet...

- Delayed deployments
- Revenue loss
- Operational burden
- Incompliance with regulations

<v-click>

Why?

</v-click>

---
layout: image
image: /old-city.png
---
## Typical container image is not a safe place:<br/> smuggler tunnels

- Package manager
- Unnecessary components -> potential exploitable paths

---
layout: image
image: /old-city.png
---
## Typical container image is not a safe place:<br/> thick fog

- Where does the image come from?
- Who is responsible for updates?
- Is there a defined update cycle?

---
layout: image
image: /old-city.png
---
## Typical container image is not a safe place:<br/> phantoms in the fog

- Vulnerabilities (CVEs): security weaknesses that can be exploited
- Hundreds of vulnerabilities
- Patches: how you can eliminate a specific phantom

---

## Not a dystopian phantasy, but reality of modern cloud deployments

- 40,003 CVEs recorded in 2024 - 39% more than in 2023
- 604 vulnerabilities in an average container image
- 44% of Java services contain known-exploited vulnerabilities
- 91% of projects contain OSS components not updated after CVEs were found and patched

---
layout: cover
---

# What do you do if your app lives in such a city?
## Three solutions: attack, stay, leave

---

## Attack outsiders first

- Knowing martial arts doesn't mean you should go looking for thugs

---

## Stay and defend the old order

- React to security incidents
- Why should you solve the issues in the code you didn't write?


---

## Leave and move to Arcology

- New container image from bottom up
- Many questions:<br/><br/>
  - Where to find a reliable base?
  - How to choose one?
  - Need to refactor everything?
  - Will it solve all the problems at once?

<br/>

<v-click>

Not so terrifying as it seems because...

</v-click>

---
layout: cover
---

## Remember we started with hardened container images? <br/> Time for them to enter the stage

---
layout: two-cols-header
---

## Hardened images: new container security standard
<br/>

<div class="hi-grid">
  <div class="hb">Low to zero CVEs</div>
  <div class="arrow">➡️</div>
  <div class="hb">Safer base from the start</div>

  <div class="hb">No package manager, minimalistic base</div>
  <div class="arrow">➡️</div>
  <div class="hb">Minimized attack surface</div>

  <div class="hb">Immutable component set</div>
  <div class="arrow">➡️</div>
  <div class="hb">No tampering with container at runtime</div>

  <div class="hb">SBOM, digital signature</div>
  <div class="arrow">➡️</div>
  <div class="hb">You know what's in the image and who made it</div>

  <div class="hb">Continuous patching</div>
  <div class="arrow">➡️</div>
  <div class="hb">The image stays safe</div>
</div>

<style>
.hi-grid{
  display:grid;
  grid-template-columns: 1fr 56px 1fr;
  row-gap: 14px; column-gap: 18px;
  align-items:center;
  max-width: 1100px;
}
.hb{
  background: #0f1424;
  border: 2px solid #00e6ff;
  border-radius: 12px;
  padding: 16px 18px;
  min-height: 64px;
  display:flex; align-items:center;
  font-size: 18px; line-height:1.3;
}
.arrow{
  text-align:center; font-size: 38px; line-height:1; font-weight: 700;
  color:#00e6ff; opacity:0.95;
}
</style>


---
layout: image-right
image: /alpaquita.jpg
---

## BellSoft's Hardened Images: Based on Alpaquita Linux

- Minimalistic
- LTS releases
- Two libc flavors: optimized musl and glibc

---
layout: image-right
image: "/logos.png"
---

## BellSoft's Hardened Images: A variety of free images

The images are available on:
- Docker Hub
- GitHub Container Registry
- Microsoft Container Registry
- Google Container Registry
- Amazon Elastic Container Registry


---

## BellSoft's Hardened Images: 3-in-1

- Runtime, OS, and container security from one team
- SLA-backed proactive patching from in-house Linux and Java experts


---

## BellSoft's Hardened Images: Beyond Pure CVE Reduction

<br/>

<div class="center-stage">
<div class="hi-grid">
  <div class="hb">OUR TEAM<br/> handles the security of your base image</div>
  <div class="arrow">→</div>
  <div class="hb">YOUR TEAM<br/> is free to focus on app's security</div>
</div>
</div>

<style>
.center-stage{
  display:grid;
  place-items:center;
  min-height: 30vh;
}

.hi-grid{
  display:grid;
  grid-template-columns: 1fr 56px 1fr;
  row-gap: 14px; column-gap: 18px;
  align-items:center;
  max-width: 1100px;
}
.hb{
  background: #0f1424;
  border: 2px solid #00e6ff;
  border-radius: 12px;
  padding: 16px 18px;
  min-height: 64px;
  display:flex; align-items:center;
  font-size: 18px; line-height:1.3;
}
.arrow{
  text-align:center; font-size: 38px; line-height:1; font-weight: 700;
  color:#00e6ff; opacity:0.95;
}
</style>


---
layout: cover
---

## The data speaks louder than words:<br/> Let's have a look, shall we?

<div class="link-wrap">
https://bell-sw.com/bellsoft-hardened-images/
</div>

<style>
.link-wrap{
  position: absolute;
  right: 32px;
  bottom: 28px;
}

</style>

---
layout: center
---

<img src="/temurin.png" width="700px" class="center"/>

<style>
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</style>

---
layout: center
---

<img src="/python.png" width="700px" class="center"/>

<style>
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</style>
---
layout: cover
---

## Here comes the most exciting part:<br/> How do you migrate to a hardened image?

---
layout: center
---

## BellSoft's Hardened Images are free to use!

<img src="/dh.png" class="center"/>

<style>
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</style>

---

## Before
<br/>

```docker
FROM openjdk:latest as builder

WORKDIR /app
ADD my-app /app/my-app
RUN cd my-app && ./mvnw package

EXPOSE 8080
ENTRYPOINT java -jar /app/my-app/target/*.jar
```

---

## After
<br/>

<v-click>Pinning by digest is recommended</v-click>

<br/>

````md magic-move
```docker
FROM bellsoft/hardened-liberica-runtime-container:jdk-25-glibc as builder

WORKDIR /app
ADD my-app /app/my-app
RUN cd my-app && ./mvnw package

FROM bellsoft/hardened-liberica-runtime-container:jre-25-glibc

WORKDIR /app
COPY --from=builder /app/my-app/target/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app/app.jar"]
```

```docker
#base image version: bellsoft/hardened-liberica-runtime-container:jdk-25-glibc
FROM bellsoft/liberica-runtime-container:sha256:226d1e0d65fdad2794924c7464ff7091cd4e0d8cd05a9886f592ecde133d93f6 as builder

WORKDIR /app
ADD my-app /app/my-app
RUN cd my-app && ./mvnw package

#base image version: bellsoft/hardened-liberica-runtime-container:jre-25-glibc
FROM bellsoft/liberica-runtime-container:sha256:58f09e3e991a4588b413394cc0400b03118b492927d413c28b872e6f57cbf6fb

WORKDIR /app
COPY --from=builder /app/my-app/target/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app/app.jar"]
```
````

---
layout: image
image: /new-city.jpg
---

---
layout: image
image: /new-city.jpg
---

## Hardened image is a safe place

- No package manager
- Minimalistic base
- You know what components are used in the image
- Low-to-zero CVEs
- Known vulnerabilities are patched by the vendor
- No patch upstream? BellSoft will make one for you!

---
layout: image
image: /new-city.jpg
---

## What's next?

- Verify the signature with cosign (can do that in CI/CD)
- Set up updates monitoring
- The base is solid, care about the new city built on it:<br/>
  - follow container security practices
  - focus on the application security

---

## TL;DR Hardened Images Integrate Well Into DevSecOps

- Clear CVE management process
- Provenance data for compliance and audits
- Shift security left without slowing down deployments
- Lower operational overhead

---

# 🔐 Hardened Images: Your New Security Baseline

## Thank you!

🦋 @cat-edelveis.bsky.social | bell-sw.com

---

## References

1. https://www.netrise.io/resources-whitepaper-brief/supply-chain-visibility-risk-study-edition-2
2. https://www.datadoghq.com/state-of-devsecops/
3. https://www.redhat.com/en/resources/kubernetes-adoption-security-market-trends-overview
4. https://www.blackduck.com/resources/analyst-reports/open-source-security-risk-analysis.html
5. https://cyberpress.org/over-40000-cves-published-in-2024/