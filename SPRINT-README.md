# Paper 6 — Operationalizing Reconstructive Authority
## Sprint README — Para retomar en cualquier sesión

> **Leer esto primero.** Tiene todo lo necesario para continuar sin contexto previo.
> **Nota completa en vault:** `traslaia-brain/proyectos/Governance Quartet/PAPER-6-SPRINT.md`

---

## Qué es Paper 6

Paper 6 es la operacionalización de RAM (Paper 5).
- Paper 5 define QUÉ es autoridad reconstructiva (teoría)
- Paper 6 define CÓMO se implementa en runtime (protocolo)

**Título:**
Operationalizing Reconstructive Authority: Runtime Construction, Dependency Resolution, and Execution Gating in Autonomous Agent Systems

---

## Estado al 2026-04-21

### ✅ Ya existe (en archivos fuente)

- Paper 6 completo (cuerpo, figuras TikZ, protocolo, teoremas)
  → `C:\Users\Mariana\Desktop\Chelo\Papers\documentos complementarios\conversacion paper 6 chatgpt.md`

- Recovery Loop (LaTeX) + Theorem 4 (Liveness) + Abstract final + Intro final
  → `C:\Users\Mariana\Desktop\Chelo\Papers\documentos complementarios\review paper 6 chatgpt.md`

- Aporte arquitectónico Grok (IML trigger + Paper 0 recovery baseline)
  → `C:\Users\Mariana\Desktop\Chelo\Papers\documentos complementarios\review paper 6 Grok.md`

### 🔲 Falta hacer

1. **T1.1** Agregar subsección "Paper 0 Reversion" al Recovery Loop (un párrafo)
2. **T1.2** Ensamblar `Paper/main.tex` completo uniendo todas las piezas
3. **T1.3** Crear `Paper/references.bib` con la serie completa P0-P5
4. **T2.1** Fix editorial: "RAM replaces ACP" → "RAM operates as criterion within ACP gate"
5. **T2.2** Fix editorial: "eliminates invalid execution" → "guarantees no action without constructible authority"
6. **T2.3** Especificar IML trigger en Drift Handling
7. **T3.x** Publicación: compilar → GitHub → Zenodo → arXiv

---

## El insight más importante que no perder

### El HALT state
```
Sistema tradicional:  ADMIT | DENY
Sistema RAM:          ADMIT | DENY | HALT (A(t) = ⊥)
```
HALT ≠ DENY.
- DENY = "sé que no"
- HALT = "no tengo información suficiente para decidir → no ejecuto"

### Paper 0 como recovery baseline (aporte Grok)
Cuando el sistema no puede adquirir más información para salir de HALT:
→ revertir al último estado atómicamente consistente (Paper 0)

### Safety + Liveness
- Safety: ninguna acción sin autoridad construible (Papers 0-6)
- Liveness (Theorem 4): si la observabilidad es recuperable → el sistema eventualmente reanuda

---

## Cómo ensamblar main.tex

1. Abrir `conversacion paper 6 chatgpt.md` — tiene el cuerpo completo en inglés
2. Copiar secciones 1-12 como esqueleto
3. Reemplazar Abstract + Introduction con las versiones de `review paper 6 chatgpt.md`
4. Insertar la sección "Recovery Loop" completa de `review paper 6 chatgpt.md` (tiene LaTeX listo)
5. Insertar Theorem 4 de `review paper 6 chatgpt.md`
6. Insertar Figures 1-4 (TikZ) de `conversacion paper 6 chatgpt.md`
7. Agregar Figure 5 (Recovery Loop) de `review paper 6 chatgpt.md`
8. Aplicar los 3 fixes editoriales (T2.1, T2.2, T2.3)
9. Agregar párrafo Paper 0 Reversion en subsección State Augmentation

---

## Estructura del directorio

```
Paper 6 - Operationalizing RAM/
├── SPRINT-README.md          ← este archivo
├── Paper/
│   ├── main.tex              ← 🔲 pendiente ensamblar
│   └── references.bib        ← 🔲 pendiente crear
└── Figures/                  ← 🔲 copiar figuras TikZ compiladas
```

---

## Integración correcta con el stack (para no confundir al ensamblar)

| Capa | Rol en Paper 6 |
|---|---|
| P0 (Atomicidad) | Safety net del Recovery Loop — revertir a último estado consistente |
| P1 (ACP) | Pipeline de enforcement — RAM es el CRITERIO dentro del gate (etapa 3), NO lo reemplaza |
| P2 (IML) | Trigger de recomputación de RAM — event-driven, no polling continuo |
| P5 (RAM) | Definición formal — Paper 6 la operacionaliza |

---

## Nota sobre Micheal Jones

Micheal Jones co-diseñó el protocolo operacional (7 pasos, decision codes, audit schema, prior guardrails).
Atribuirlo como: "operational refinement" o "personal communication, M. Jones, 2026" si es necesario citar.
NO presentarlo como contribución separada en el paper.
