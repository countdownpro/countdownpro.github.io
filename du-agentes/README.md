# Cómo disparar el sistema cuando prendas la compu

## 1. Instalar (una vez, 5 minutos)
```bash
# Si no tenés Claude Code instalado:
npm install -g @anthropic-ai/claude-code

# Traer esta carpeta a la compu
git clone https://github.com/countdownpro/countdownpro.github.io.git
cp -r countdownpro.github.io/du-agentes ~/du-agentes
cd ~/du-agentes && git init && git add . && git commit -m "Sistema de agentes du."
```
(Si preferís, después la subís a un repo privado `du-agentes` y la sacás de acá.)

## 2. Cargar insumos
- `biblioteca/`: libros, Golden Circle y el resto de la bibliografía.
- Por cada cliente: `/nuevo-cliente caritas` y dejar transcripts en `clientes/caritas/00-fuentes/`.

## 3. Conectores (en Claude Code: `/mcp`)
Verificá que estén Google Drive, Granola, Supermetrics y Adobe. Son los mismos que ya usás en claude.ai.

## 4. Disparar, en este orden
```bash
cd ~/du-agentes && claude
```
1. `/biblia-du` : el Estratega escribe cómo piensa du. Lo revisás y aprobás.
2. `/pedido arrancá Cáritas` : el Gestor detecta fase 1 y llama al Estratega.
3. Contestás las preguntas (transcript o doc en `03-respuestas/`) y `/pedido seguí con Cáritas`.
4. `/metricas-mensual` : primera corrida manual para calibrar.

## 5. Automatizar el día 2 de cada mes
En la app de escritorio de Claude: tarea programada con el prompt `/metricas-mensual` en la carpeta `~/du-agentes`.
Alternativa con cron (la compu tiene que estar prendida):
```bash
0 9 2 * * cd ~/du-agentes && claude -p "/metricas-mensual" >> _cola/metricas.log 2>&1
```

## Regla de oro
Hablale siempre al Gestor con `/pedido`. Él lee el estado de cada cliente, así no tenés que reexplicar nada.
