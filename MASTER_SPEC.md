# izi-resume — Master Product Specification

## 0. Purpose

This repository contains a single-scene interactive visual-novel-style resume.

The experience is intentionally built as a contrast:

- the visual layer is cinematic, surreal and technically ambitious;
- the resume content is dry, factual and professional;
- the user navigates through exactly seven visual-novel pages/scenes;
- the final page becomes the complete resume view.

This is NOT a generic SaaS landing page.
This is NOT a game.
This is NOT a terminal emulator.
This is NOT a conventional portfolio grid.
This is NOT a Minecraft-style environment.

The implementation must preserve the concept rather than normalize it into a conventional web portfolio.

---

## 1. Source of Truth for Personal Information

`RESUME.md` is the sole authoritative source for:

- name
- title
- employment
- experience
- projects
- technologies
- skills
- dates
- education
- contacts
- metrics
- cloud technologies
- any other personal/resume information

Agents MUST NOT invent, infer, embellish or silently correct personal information.

If something is not explicitly supported by `RESUME.md`, it must not appear as resume content.

If a visual metaphor requires an exact technology name, the name must be read from `RESUME.md`.

---

## 2. Visual Concept

The application is one continuous ocean world.

The ocean remains the persistent visual environment while the scene evolves between pages.

The visual language is cinematic and realistic.

All generated 3D assets must belong to one coherent art direction.

Do not combine obviously unrelated asset-pack styles.

The visual quality target is final-product quality, not prototype quality.

Do not accept primitive placeholder geometry as a final implementation.

---

## 3. Kanye Character

Kanye is a 2D photographic narrator.

Kanye is NOT a 3D character.

Do NOT build:

- skeletons
- rigging
- 3D facial animation
- lip sync
- 3D character shaders
- 3D character physics

Use photographic 2D imagery.

Different photographs can represent different scenes, poses and facial expressions.

The images must be integrated into the scene composition so they feel intentional rather than like arbitrary HTML stickers.

Kanye is silent.

There must be:

- no Kanye dialogue
- no Kanye speech bubbles
- no Kanye biography
- no Kanye quotes
- no generated Kanye monologue

Kanye functions as the visual narrator.

The application may transition between photographic states with subtle crossfade, motion, scale, parallax or compositional changes.

There is NO requirement to keep a particular historical Kanye visual era.

Use the selected photographic assets as the visual source.

---

## 4. Seven Pages

There are exactly seven visual-novel pages.

Navigation:

- previous
- next
- page indicator
- keyboard navigation may be supported

There are six forward transitions from the first page to the final page.

Do not turn the seven pages into a scrolling web page.

The seventh page is special.

On page seven:

- the 3D world leaves the foreground;
- the ocean/objects/character transition away;
- the dialogue cloud expands to occupy the viewport;
- the complete resume becomes readable;
- the same visual language is preserved;
- PDF download remains available.

---

## 5. Dialogue Cloud

The dialogue cloud is DOM/HTML.

It is NOT a 3D mesh.

It contains real selectable text.

The dialogue cloud is the main resume-content surface.

The first six pages contain distributed resume content.

The distribution must be derived from `RESUME.md`.

Do not invent sections.

Do not invent narrative prose.

Do not rewrite factual resume information into marketing copy.

The seventh page contains the complete resume.

The DOM must retain the resume text even when WebGL/WebGPU is unavailable.

---

## 6. Visual Metaphors

The following visual metaphors are part of the concept.

Do not add unrelated DevOps mascots or new technology metaphors unless explicitly added to the project specification later.

### Docker

Docker is represented by a realistic whale carrying shipping containers.

The whale must read visually as a real whale.

The containers provide the Docker visual association.

A major event is the whale entering/impacting the ocean.

The event should produce convincing:

- body displacement
- splash
- foam
- spray
- secondary waves
- local ripples

Do not fake the event with a simple object teleport.

---

### Kubernetes

Kubernetes is represented by a realistic ship.

It is NOT a pirate ship.

The Kubernetes visual identity is represented through a recognizable Kubernetes-wheel/helm-like steering wheel element integrated into the ship.

The ship must behave like a real floating ship.

The ship controls multiple Docker whales.

Chains visibly connect the ship and whales.

Chains should:

- attach to believable points
- sag/tension naturally
- react to movement
- avoid obvious intersection artifacts

The system is cinematic and controlled, not a general-purpose rigid-body sandbox.

---

### Linux

Linux is represented by a realistic penguin on an ice floe.

The penguin slides across the ice.

The penguin eventually falls/splashes into the ocean.

The visual metaphor should work without explanatory text.

---

### Cloud Tools

Clouds are used as the visual category for cloud technologies.

Exact cloud technology names MUST come from `RESUME.md`.

Never invent cloud technologies to populate the scene.

Cloud labels must remain visually subordinate to the cinematic environment.

---

### Argo CD

Argo CD is represented by a realistic octopus.

It is an OCTOPUS.

Do not turn it into a kraken or fantasy monster.

The octopus emerges from the water and pulls the Kubernetes ship beneath the surface.

The underwater pull should be physically convincing:

- tentacle attachment
- ship reaction
- water displacement
- underwater transition
- bubbles/foam where appropriate
- changing visibility
- depth/atmosphere

---

## 7. Ocean

The ocean is the central rendering system.

It must not be a static blue plane.

The target system includes:

- large-scale waves
- medium/small waves
- directional wave motion
- physically plausible surface response
- reflections/specular response
- Fresnel behavior
- foam
- spray
- local disturbances
- object interaction
- atmospheric integration

Where practical, GPU-driven simulation should be used for local water disturbances.

The implementation must remain performant.

Do not implement a full general-purpose fluid simulator unless it is genuinely required.

Prefer controlled cinematic simulation.

---

## 8. Object/Ocean Interaction

Objects should visually interact with the ocean.

Relevant systems include:

- buoyancy
- wave sampling
- surface normals
- pitch/roll response
- local displacement
- splash events
- foam rings
- spray particles
- secondary ripples
- underwater transitions

The system should be deterministic enough for cinematic scene transitions.

---

## 9. Rendering

Primary stack:

- React
- TypeScript
- Vite
- Three.js
- React Three Fiber

WebGPU may be used where beneficial.

WebGL2 fallback is required for critical functionality.

Do not make the entire product unusable merely because WebGPU is unavailable.

Critical effects must have a fallback strategy.

---

## 10. Asset Pipeline

Preferred asset representation:

- GLB/GLTF
- optimized geometry
- compressed textures where appropriate
- LOD where appropriate
- reasonable draw-call count

Generated assets must be optimized before integration.

Asset generation and asset integration are separate concerns.

A generated source asset is not automatically a production-ready asset.

Each asset must be checked for:

- scale
- orientation
- topology
- material correctness
- texture resolution
- UV correctness
- animation correctness
- file size
- runtime performance
- visual consistency

---

## 11. Cinematic Direction

The scene is controlled by a scene director/timeline system.

Do NOT implement page transitions using scattered `setTimeout()` calls.

Use explicit scene state and timeline/event abstractions.

Conceptually:

Scene
  -> environment state
  -> character state
  -> object state
  -> camera state
  -> event timeline
  -> dialogue state

A transition may contain:

1. dialogue transition
2. Kanye photographic transition
3. camera movement
4. object entrance
5. physical/cinematic event
6. ocean response
7. final composition
8. dialogue reveal

---

## 12. React Architecture

React state controls:

- page
- scene state
- UI state
- accessibility state
- loading state
- fallback state

Do NOT update React state every animation frame.

Per-frame systems belong in the rendering layer.

Use appropriate Three.js/R3F mechanisms for:

- animation
- shader uniforms
- object transforms
- physics state
- particle state
- camera motion

---

## 13. Camera

The camera is cinematic.

Do NOT expose free camera rotation as the primary interaction.

No OrbitControls as the main experience.

Small controlled camera motion is allowed.

Desktop and mobile may use separate composition profiles.

---

## 14. UI

UI must be minimal.

Required concepts:

- name/title area
- PDF download
- dialogue cloud
- page indicator
- previous/next navigation

Avoid:

- generic SaaS cards
- excessive rounded rectangles
- glassmorphism
- dashboard layouts
- skill badges
- marketing hero copy
- terminal UI
- decorative UI noise

The visual spectacle belongs to the scene, not to a collection of cards.

---

## 15. Accessibility / Fallback

Resume content must exist in real DOM text.

If WebGL/WebGPU cannot render:

- show the resume content
- preserve navigation
- preserve PDF access
- do not show an empty screen

Canvas is an enhancement, not the sole source of resume information.

---

## 16. Mobile

Desktop is the primary composition.

Mobile requires a dedicated composition profile.

On mobile:

- reduce particle density
- reduce shadow quality where required
- reduce render resolution where required
- reduce expensive post-processing where required
- simplify composition rather than merely shrinking desktop geometry

The resume must remain readable.

---

## 17. Performance

Performance is part of correctness.

Measure:

- frame rate
- GPU frame time where available
- memory
- asset load time
- shader compilation time
- scene transition cost

Use:

- frustum culling
- LOD
- instancing where appropriate
- compressed assets
- lazy loading where appropriate
- preload critical assets
- controlled particle counts

Do not optimize blindly.

Measure before and after significant optimization.

---

## 18. Quality Gate

A feature is not complete merely because:

- TypeScript compiles
- tests pass
- the browser loads

Visual acceptance is mandatory.

The final result must be judged for:

- composition
- realism
- lighting
- animation
- material quality
- water interaction
- asset consistency
- transition quality
- typography
- readability

Do not declare a cinematic feature complete with an obviously primitive placeholder.

---

## 19. No Scope Creep

Do not add:

- unrelated technologies
- unrelated mascots
- unrelated game mechanics
- terminal emulators
- music
- achievements
- inventory
- WASD controls
- fake dashboards
- generic portfolio sections
- invented resume information

If a new idea appears, record it as a discovered issue or proposal rather than silently adding it.

