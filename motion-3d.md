# 3D Motion & Animation Tools for Ballroom Dance

[日本語版はこちら / Japanese](motion-3d.ja.md) · [Back to Awesome Ballroom Dance](README.md)

Open-source tools for turning ballroom / Latin dancing into **3D motion data and teaching videos** — showing footwork, floor patterns, and body sway / rotation for the International Style 10 Dances. ⭐ badges show live GitHub star counts (via shields.io).

No single project covers all 10 dances yet. A practical pipeline is: **capture** (video → 3D motion) → **reuse ballroom motion data** where available → **render** (Blender or the browser) with footprints, sway arrows, and counts.

## Contents

- [Video to 3D motion (motion capture)](#video-to-3d-motion-motion-capture)
- [Ballroom & partner-dance motion data / research](#ballroom--partner-dance-motion-data--research)
- [Rendering & teaching videos](#rendering--teaching-videos)
- [Music-to-dance generation (reference)](#music-to-dance-generation-reference)
- [Suggested workflow](#suggested-workflow)

---

## Video to 3D motion (motion capture)

Extract skeletal motion (SMPL / BVH / FBX) from video of a teacher's demonstration. For sway, choose methods that recover torso tilt relative to gravity and the floor.

- [GVHMR](https://github.com/zju3dv/GVHMR) ![GitHub stars](https://img.shields.io/github/stars/zju3dv/GVHMR?style=flat&label=%E2%AD%90) - World-grounded human motion recovery from monocular video in gravity-view coordinates (SIGGRAPH Asia 2024); body tilt relative to gravity makes it well suited to visualizing sway.
- [WHAM](https://github.com/yohanshin/WHAM) ![GitHub stars](https://img.shields.io/github/stars/yohanshin/WHAM?style=flat&label=%E2%AD%90) - World-grounded 3D human motion and global trajectory from monocular video; useful for checking floor travel and step direction.
- [4D-Humans](https://github.com/shubham-goel/4D-Humans) ![GitHub stars](https://img.shields.io/github/stars/shubham-goel/4D-Humans?style=flat&label=%E2%AD%90) - Reconstructs and tracks multiple people in video with transformers (HMR 2.0); handles couples.
- [FreeMoCap](https://github.com/freemocap/freemocap) ![GitHub stars](https://img.shields.io/github/stars/freemocap/freemocap?style=flat&label=%E2%AD%90) - Free markerless motion capture with ordinary multi-camera setups; Blender export. Good for studio recording.
- [EasyMocap](https://github.com/zju3dv/EasyMocap) ![GitHub stars](https://img.shields.io/github/stars/zju3dv/EasyMocap?style=flat&label=%E2%AD%90) - Multi-view markerless motion capture toolbox for higher accuracy.

## Ballroom & partner-dance motion data / research

- [Dancing Points](https://github.com/PeizhuoLi/dancing-points) ![GitHub stars](https://img.shields.io/github/stars/PeizhuoLi/dancing-points?style=flat&label=%E2%AD%90) - Synthesizes full-body leader and follower ballroom motion from three-point VR input (Computer Graphics Forum 2026); releases motion-captured couple data in FBX (incl. cha-cha, foxtrot, Viennese waltz) and a [Unity playback project](https://github.com/PeizhuoLi/dancing-points-unity) ![GitHub stars](https://img.shields.io/github/stars/PeizhuoLi/dancing-points-unity?style=flat&label=%E2%AD%90).
- [Duolando](https://github.com/lisiyao21/Duolando) ![GitHub stars](https://img.shields.io/github/stars/lisiyao21/Duolando?style=flat&label=%E2%AD%90) - Follower motion generation for duet dance (ICLR 2024) with the DD100 duet dataset.
- [interDance_API](https://github.com/inter-dance/interDance_API) ![GitHub stars](https://img.shields.io/github/stars/inter-dance/interDance_API?style=flat&label=%E2%AD%90) - Rendering code for the InterDance duet dance dataset ([paper](https://arxiv.org/abs/2412.16982)).
- [BDD](https://github.com/matsuyhit/BDD) ![GitHub stars](https://img.shields.io/github/stars/matsuyhit/BDD?style=flat&label=%E2%AD%90) - Introduction to and analysis of the HASC Ballroom Dance Dataset.

## Rendering & teaching videos

- [Blender](https://github.com/blender/blender) ![GitHub stars](https://img.shields.io/github/stars/blender/blender?style=flat&label=%E2%AD%90) - Import FBX / BVH and render videos; with Python scripting add floor footprints, pelvis / head trajectories, spine-tilt (sway) arrows, and S / Q / & count captions.
- [three.js](https://github.com/mrdoob/three.js) ![GitHub stars](https://img.shields.io/github/stars/mrdoob/three.js?style=flat&label=%E2%AD%90) - Browser 3D library for interactive lessons (orbit camera, slow motion, loop a figure).
- [three-vrm](https://github.com/pixiv/three-vrm) ![GitHub stars](https://img.shields.io/github/stars/pixiv/three-vrm?style=flat&label=%E2%AD%90) - Use VRM avatars in three.js to present dance motion with a character model.

## Music-to-dance generation (reference)

These generate dance from music, but are trained mainly on solo street / pop dance (AIST++), so they do not produce correct 10-dance figures or sway. Use captured or motion-captured data for teaching material.

- [EDGE](https://github.com/Stanford-TML/EDGE) ![GitHub stars](https://img.shields.io/github/stars/Stanford-TML/EDGE?style=flat&label=%E2%AD%90) - Editable dance generation from music with diffusion (CVPR 2023).
- [Bailando](https://github.com/lisiyao21/Bailando) ![GitHub stars](https://img.shields.io/github/stars/lisiyao21/Bailando?style=flat&label=%E2%AD%90) - 3D dance generation with an actor-critic GPT and choreographic memory (CVPR 2022).

## Suggested workflow

1. Record the teacher's demonstration with 2–4 cameras (FreeMoCap) or one camera (GVHMR).
2. Import the exported motion into Blender.
3. Overlay footprints, sway angle, and counts.
4. Render one video per dance and figure.
