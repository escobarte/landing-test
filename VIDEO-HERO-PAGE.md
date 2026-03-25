# Video Hero Page — Transnatur INC

## Цель страницы

Одностраничный HTML — **выбор пути**.  
Посетитель видит видео на фоне и два варианта:
- **I'm a Driver** → ведёт на `index.html` (лендинг для водителей)
- **I'm a Customer** → ведёт на страницу клиентов (позже)

Референс стиля: https://goamericars.com/

---

## Файл

```
video-hero.html   ← создать в корне проекта
```

Видео файл уже есть:
```
assets/vide_truck.mp4
```

---

## Структура страницы

```
[ FULLSCREEN VIDEO BACKGROUND ]
         ↕ dark overlay
   [ LOGO — белый, по центру сверху ]
   
   [ HEADLINE ]
   "Built for the Road. Trusted Nationwide."
   
   [ SUBTEXT ]
   "Choose your path to get started."
   
   [ BUTTON 1 ]  [ BUTTON 2 ]
   "I'm a Driver"   "I'm a Customer"
```

---

## Технические требования

### Video Background
```html
<video autoplay muted loop playsinline>
  <source src="assets/vide_truck.mp4" type="video/mp4">
</video>
```

**Обязательно:**
- `autoplay` — запускается сразу
- `muted` — без звука (иначе браузер заблокирует autoplay)
- `loop` — зацикленное видео
- `playsinline` — работает на iOS

### CSS для видео на фоне
```css
.video-container {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  z-index: -1;
  overflow: hidden;
}

.video-container video {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.overlay {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: linear-gradient(
    rgba(11, 31, 58, 0.65),
    rgba(11, 31, 58, 0.80)
  );
  z-index: 0;
}
```

---

## Дизайн

### Шрифты (из SKILL-landing-brief.md)
```html
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@800&family=Bebas+Neue&display=swap" rel="stylesheet">
```

- Headline → `Poppins 800`, белый, uppercase
- Subtext → `Bebas Neue 400`, светло-серый, letter-spacing
- Кнопки → `Poppins 800`

### Цвета (из SKILL-landing-brief.md)
```css
:root {
  --navy:    #0B1F3A;
  --red:     #C62828;
  --red-hover: #A31515;
  --white:   #FFFFFF;
}
```

### Кнопки
```
"I'm a Driver"    → красная (#C62828), белый текст
"I'm a Customer"  → прозрачная (outline), белая рамка и текст
```

```css
.btn-primary {
  background: var(--red);
  color: white;
  border: none;
  padding: 18px 48px;
  font-family: 'Poppins', sans-serif;
  font-weight: 800;
  font-size: 1.1rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.2s, transform 0.15s;
}
.btn-primary:hover {
  background: var(--red-hover);
  transform: translateY(-2px);
}

.btn-outline {
  background: transparent;
  color: white;
  border: 2px solid white;
  padding: 18px 48px;
  font-family: 'Poppins', sans-serif;
  font-weight: 800;
  font-size: 1.1rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.2s, transform 0.15s;
}
.btn-outline:hover {
  background: rgba(255,255,255,0.1);
  transform: translateY(-2px);
}
```

### Контент по центру
```css
.content {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  text-align: center;
  padding: 0 24px;
}
```

---

## Анимация при загрузке

Элементы появляются с задержкой (staggered):
```css
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(24px); }
  to   { opacity: 1; transform: translateY(0); }
}

.logo      { animation: fadeUp 0.6s ease 0.1s both; }
.headline  { animation: fadeUp 0.6s ease 0.3s both; }
.subtext   { animation: fadeUp 0.6s ease 0.5s both; }
.buttons   { animation: fadeUp 0.6s ease 0.7s both; }
```

---

## Текст

```
Logo:      Transnatur INC (белый логотип)
Headline:  BUILT FOR THE ROAD. TRUSTED NATIONWIDE.
Subtext:   Choose your path to get started.
Button 1:  I'M A DRIVER        → href="index.html"
Button 2:  I'M A CUSTOMER      → href="#" (пока заглушка)
```

---

## Mobile

```css
@media (max-width: 600px) {
  .headline { font-size: 2rem; }
  .buttons  { flex-direction: column; gap: 16px; }
  .btn-primary, .btn-outline { width: 100%; }
}
```

---

## Промпт для Claude Code

```
Read SKILL-landing-brief.md and VIDEO-HERO-PAGE.md, then create video-hero.html.

Requirements:
- Full-screen looping video background using assets/vide_truck.mp4
- Dark navy overlay on top of video
- Centered content: white Transnatur logo, bold headline, subtext, two buttons
- Button 1 "I'M A DRIVER" → red, links to index.html
- Button 2 "I'M A CUSTOMER" → outline white, href="#" placeholder
- Staggered fade-up animation on page load
- Fully responsive (mobile-first)
- Use fonts, colors and brand rules from SKILL-landing-brief.md
```
