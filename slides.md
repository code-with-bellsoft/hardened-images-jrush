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
## Typical container image is not a safe place:<br/> smuggler tunnels

- Package manager
- Unnecessary components -> potential exploitable paths

---
layout: image
image: /old-city.png
---
## Typical container image is not a safe place:<br/> thick fog

- No SBOM, no digital signature:<br/><br/>
    - Where does the image come from?
    - Who is responsible for updates?
    - Is there a defined update cycle?

---
layout: image
image: /old-city.png
---
## Typical container image is not a safe place:<br/> phantoms in the fog

- CVEs: dozens? hundreds?<br/><br/>
    - Scanners are paranoid, but not always efficient
    - Specific weapon for each phantom -> Patches
    - What if there's no patch upstream?

---

## Not a dystopian phantasy, but reality of modern cloud deployments

- 40,003 CVEs recorded in 2024 (39% more than in 2023)
- 604 vulnerabilities in an average container image
- 12.4% of components are manifestless
- 44% of Java services contain known-exploited vulnerabilities
- 91% of projects contain outdated OSS components
- Most vulnerabilities in Debian packages

---
layout: cover
---

## One would probably get away with that, but...

---

## No way for normal operation in a broken reality

- Delayed deployments
- Revenue loss
- Operational burden
- Broken SLAs
- Incompliance with regulations

---
layout: cover
---

## Three solutions: attack, stay, leave

---

## Attack outsiders first

- No idea who to attack
- No idea how to attack

---

## Stay and defend the old order

- Most teams do that now
- Look for patches reactively
- React to security incidents
- Block deploys if smth is wrong
- Scan -> patch -> scan -> patch -> scan ...


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
  <div class="arrow">→</div>
  <div class="hb">Safer base from the start</div>

  <div class="hb">No package manager or unrequired libs</div>
  <div class="arrow">→</div>
  <div class="hb">Minimized attack surface</div>

  <div class="hb">Immutable component set</div>
  <div class="arrow">→</div>
  <div class="hb">No tampering with container at runtime</div>

  <div class="hb">SBOM, digital signature</div>
  <div class="arrow">→</div>
  <div class="hb">Clear provenance</div>

  <div class="hb">Continuous patching</div>
  <div class="arrow">→</div>
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

## BellSoft's Hardened Images: Beyond Pure CVE Reduction

- Based on Alpaquita Linux musl/glibc
- Images for OpenJDK, Go, Python, GraalVM, C/C++
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
  <a
    href="https://bell-sw.com/bellsoft-hardened-images/"
    target="_blank" rel="noopener noreferrer"
  >
    Live container image CVEs stats ↗
  </a>
</div>

<style>
.link-wrap{
  position: absolute;
  right: 32px;
  bottom: 28px;
}

</style>


---
layout: cover
---

## Here comes the most exciting part:<br/> How do you migrate to a hardened image?

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

- No smuggler tunnels
- No fog, the air is clear
- No lurking phantoms
- If a phantom appears, it is seen instantly and eliminated promptly
- No patch upstream? BellSoft will make one for you!

---
layout: image
image: /new-city.jpg
---

## What's next?

- Verify the signature with cosign (can do that in CI/CD)
- Set up updates monitoring: Dependabot, Renovate, etc.
- The base is solid, care about the new city built on it:<br/>
  - follow container security practices
  - focus on the application security

---

## TL;DR Hardened Images are a Perfect Match for DevSecOps

- Clear CVE management process
- Provenance data for compliance and audits
- Shift security left without slowing down deployments
- Lower operational overhead

---

# 🔐 Hardened Images: Your New Security Baseline

## Thank you!

🦋 @cat-edelveis.bsky.social | bell-sw.com