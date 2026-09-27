# 3D Globe Card Gallery

An interactive 3D gallery where cards orbit a wireframe globe. Image cards are distributed across three concentric spherical layers (Fibonacci sphere algorithm), always facing the center — drag to rotate the whole system, click any card to open a full-size detail view with a 3D mouse-tilt effect.

## Features

- **Fibonacci-sphere card layout** — cards evenly distributed across 3 depth layers (radii 12/16/20) around a central wireframe globe
- **Clickable cards** — click a floating card to open a detail modal with smooth spring animation
- **3D tilt on hover** — modal card tilts in perspective based on mouse position; favorite (heart) and download actions included
- **Orbit navigation** — drag to rotate, scroll to zoom (distance 5–40), right-drag to pan
- **Starfield backdrop** — animated WebGL star field with night-environment lighting
- **Shared card state** — React context (`CardProvider`) drives card data, selection, and modal
- **shadcn/ui + Tailwind** styling with dark space theme

## Tech Stack

- [Next.js 15](https://nextjs.org) (App Router) + React 19 + TypeScript
- [three.js](https://threejs.org) via [@react-three/fiber](https://docs.pmnd.rs/react-three-fiber) and [@react-three/drei](https://github.com/pmndrs/drei)
- [Tailwind CSS 3](https://tailwindcss.com) + [shadcn/ui](https://ui.shadcn.com) components
- [Lucide](https://lucide.dev) icons
- Originally generated with [v0.app](https://v0.app)

## Quick Start

```bash
# install dependencies
npm install

# run the dev server
npm run dev
# open http://localhost:3000
```

Build for production:

```bash
npm run build
npm start
```

## Customizing

Edit the `cards` array in `components/card-context.tsx` — each card has `id`, `imageUrl`, `alt`, and `title`. The sphere layout auto-adjusts to any number of cards:

```ts
{
  id: "1",
  imageUrl: "https://example.com/card.png",
  alt: "Card title",
  title: "Card title",
}
```

## Project Structure

```
3-d-globe-card-gallery/
├── app/
│   ├── page.tsx        # Main scene (Canvas, orbit controls, overlay)
│   ├── layout.tsx      # Root layout (theme provider)
│   └── globals.css     # Tailwind base styles
├── components/
│   ├── card-galaxy.tsx         # Fibonacci-sphere card positioning
│   ├── floating-card.tsx       # Single card mesh (clickable)
│   ├── card-modal.tsx          # Detail modal with 3D tilt + actions
│   ├── card-context.tsx        # Card data + selection state (context)
│   ├── starfield-background.tsx
│   └── ui/                     # shadcn/ui primitives
├── lib/
│   └── utils.ts
└── public/             # Static placeholder assets
```

## Environment Variables

None required. All rendering is client-side in the browser.

## Deployment Notes

This is a Next.js App Router application (no static export configured), so it needs a Node.js server runtime such as [Vercel](https://vercel.com) or [Netlify](https://netlify.com):

```bash
npm install
npm run build
npm start
```

The build ignores lint and TypeScript errors by design (`next.config.mjs`).

---

Built by Girish Lade · https://ladestack.in
