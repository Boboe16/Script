# Code Highlights for Presentation

Here are key code highlights that showcase the technical implementation behind the website:

---

## 1. Animation System with Anime.js

```tsx
useEffect(() => {
    if (hasMounted && ShoeEventCardContentRef.current) {
        document.body.style.overflow = 'hidden';
        // Staggered Children Animation
        anime.timeline()
        .add({
            targets: ShoeEventCardContentRef.current,
            translateY: ['100%', '0%'],
            opacity: [0, 1],
            easing: 'easeOutQuad',
            duration: 800,
        })
        .add({
            targets: ShoeEventCardContentRef.current.querySelectorAll('.animate-item'),
            opacity: [0, 1],
            translateY: [30, 0],
            easing: 'easeOutExpo',
            duration: 600,
            delay: anime.stagger(100),
        });
    }
}, [hasMounted]);
```

**Explanation**: Smooth, staggered animations for modal content using Anime.js, enhancing user experience with professional entrance effects.

---

## 2. Responsive Design Implementation

```tsx
const isDesktop = useMediaQuery({ query: '(min-width: 640px)' });

{!isDesktop && (
    <div className="flex flex-col gap-7 px-6 py-10 items-center justify-center h-full">
        {/* Mobile-specific content */}
    </div>
)}

{isDesktop && (
    <div className="flex flex-row gap-10 px-16 py-10 items-center justify-center h-full max-w-7xl mx-auto">
        {/* Desktop-specific content */}
    </div>
)}
```

**Explanation**: Utilizes `react-responsive` for conditional rendering to support adaptive mobile and desktop layouts.

---

## 3. 3D Model Integration with Three.js

```tsx
export default function App() {
  const isDesktop = useMediaQuery({ query: '(min-width: 640px)' });

  return (
    <Canvas style={{ width: '100%', height: '300px', touchAction: 'pan-y', pointerEvents: 'none' }}>
      <PerspectiveCamera makeDefault fov={isDesktop ? 8 : 10} position={[1.3, 1.8, 0.6]} />
      <ambientLight intensity={3} />
      <directionalLight position={[10, 10, 5]} intensity={2} castShadow />
      <OrbitControls autoRotate autoRotateSpeed={2} enablePan={false} enableZoom={false} enableRotate={false}/>
      <Model />
    </Canvas>
  );
}
```

**Explanation**: Displays interactive 3D shoe models using React Three Fiber with responsive camera control and automatic rotation.

---

## 4. Custom Font Implementation

```tsx
import { Playfair_Display, Montserrat } from 'next/font/google';

const playfair = Playfair_Display({
  subsets: ['latin'],
  weight: ['400', '500', '600', '700'],
  variable: '--font-playfair',
  display: 'swap',
});

const montserrat = Montserrat({
  subsets: ['latin'],
  weight: ['400', '500', '600'],
  variable: '--font-montserrat',
  display: 'swap',
});

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="en" className={`${playfair.variable} ${montserrat.variable}`}>
      {/* ... */}
    </html>
  );
}
```

**Explanation**: Uses Next.js optimized font system for Playfair Display and Montserrat, improving loading performance and visual identity.

---

## 5. Tailwind Configuration for Brand Colors

```ts
export default {
  theme: {
    extend: {
      fontFamily: {
        playfair: ['var(--font-playfair)'],
        montserrat: ['var(--font-montserrat)'],
      },
      colors: {
        primary: "#1D1912",
        secondary: "#F3F3E6",
        tertuary: "#EECD5C",
        quartery: "#D2A63C",
        quinary: "#BB8525",
      },
    },
  },
} satisfies Config;
```

**Explanation**: Tailwind theme extension for consistent brand styling, including custom fonts and a palette based on brand identity.

---

## 6. Interactive Header Animation

```tsx
<div className="flex flex-row gap-1 items-center group">
    <Image
        src={`/logo.png`}
        alt='logo.png'
        width={35}
        height={35}
        className="transition-all duration-500 group-hover:rotate-12 group-hover:scale-110"
    />
    {"ARIKINA".split("").map((letter, index) => (
        <h1
            key={index}
            className="font-montserrat text-secondary text-3xl hover:text-tertuary transition-all duration-300"
            style={{
                animationDelay: `${index * 0.1}s`,
                transform: `translateY(${Math.sin(index) * 2}px)`
            }}
        >
            {letter}
        </h1>
    ))}
</div>
```

**Explanation**: Each header letter is animated individually with hover effects and vertical wave-like spacing, enhancing branding and engagement.

---

These highlights showcase a range of advanced front-end techniques used in the development of the website—from animations and responsiveness to 3D integration, branding, and custom UI components.
