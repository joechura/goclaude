# Motion: parallax + counting numbers (default on, always accessible)

Every site gets two motion patterns by default: **parallax depth** on hero/feature imagery and **numbers that count up** when they scroll into view. Both must fully respect `prefers-reduced-motion` and never hide content when JS fails.

## Rules
- Motion explains or adds depth. One signature motion per section, max. No bouncing, no spinning, no motion on body text.
- Duration 600–1400ms for counters, easing `cubic-bezier(.2,.7,.2,1)`. Parallax offset small (≤ 15% of element height).
- **Reduced motion:** counters render the final number instantly; parallax is static. No exceptions.
- **No-JS / crawler:** the real final number is in the HTML. JS only animates *from* 0 *to* it.
- Screen readers hear the final number once: put the animated digits in `aria-hidden="true"` and the real value in visually-hidden text.
- Every counted number needs a real source (see SKILL.md). Format with `Intl.NumberFormat`; keep suffixes like `+`, `K`, `mi` outside the animated span.
- Animate `transform`/`opacity` only. Nothing that shifts layout (CLS).
- Never autoplay video with sound. Background video: `muted loop playsinline`, a poster image, a visible pause button, and no autoplay under reduced motion.

## Counter (drop-in, framework-free)

```html
<p class="stat">
  <span class="stat-num" data-count="25000" aria-hidden="true">25,000</span><span aria-hidden="true">+</span>
  <span class="sr-only">More than 25,000</span>
  <span class="stat-label">athletes in 2025</span>
</p>
<script type="module">
  const reduce = matchMedia('(prefers-reduced-motion: reduce)').matches;
  const fmt = new Intl.NumberFormat();
  const ease = t => 1 - Math.pow(1 - t, 3);
  const run = el => {
    const end = Number(el.dataset.count), dur = 1200, t0 = performance.now();
    const tick = now => {
      const p = Math.min((now - t0) / dur, 1);
      el.textContent = fmt.format(Math.round(end * ease(p)));
      if (p < 1) requestAnimationFrame(tick);
    };
    el.textContent = '0';
    requestAnimationFrame(tick);
  };
  if (!reduce) {
    const io = new IntersectionObserver(entries => entries.forEach(e => {
      if (e.isIntersecting) { run(e.target); io.unobserve(e.target); }
    }), { threshold: 0.6 });
    document.querySelectorAll('[data-count]').forEach(el => io.observe(el));
  }
</script>
```

## Parallax (CSS-first, scroll-driven, progressive)

```css
.parallax { overflow: clip; }
.parallax > img { scale: 1.15; }
@supports (animation-timeline: view()) {
  @media (prefers-reduced-motion: no-preference) {
    .parallax > img {
      animation: drift linear both;
      animation-timeline: view();
    }
    @keyframes drift { from { translate: 0 -7%; } to { translate: 0 7%; } }
  }
}
```
Browsers without scroll-driven animations simply show a static image, which is fine. Don't add a JS scroll-listener fallback.

## Reveal on scroll (optional, use sparingly)
Same pattern as parallax with `animation-timeline: view(); animation-range: entry 0% cover 30%;` animating opacity 0→1 and translate 16px→0. Under reduced motion or no support, content is simply visible. Never start content at `opacity:0` without the `@supports` + media guard.

## Utility
```css
.sr-only{position:absolute;width:1px;height:1px;padding:0;margin:-1px;overflow:hidden;clip:rect(0,0,0,0);white-space:nowrap;border:0}
```
