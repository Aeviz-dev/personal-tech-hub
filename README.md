Personal Tech Hub

A personal engineering and technology archive for documenting projects, experiments, and technical learning.

Status

Stage 2 — Visual identity redesign: Neon Nocturne · Full Terminal Interface. The system bar, navigation, hero window, project-structure example, archive overview, and status line are in place. Content is intentionally empty and will be added as it is created.

Tech stack
HTML5
CSS3 (custom properties for design tokens)
Git and GitHub, with GitHub Pages for future deployment

The current homepage loads no JavaScript. No frameworks are used.

Project structure
personal-tech-hub/
├── assets/
│   ├── icons/
│   └── images/
├── css/
│   ├── components.css
│   ├── responsive.css
│   └── style.css
├── js/
│   └── main.js
├── pages/
│   ├── about.html
│   ├── contact.html
│   ├── knowledge.html
│   ├── projects.html
│   └── tech-lab.html
├── index.html
└── readme.md

Files the current index.html actually loads: css/style.css and css/components.css.

Not loaded by the homepage and not modified in this stage: css/responsive.css, js/main.js, and everything in pages/. The pages exist as files but are not linked from the navigation yet; they are planned for Stage 4.

The "project-structure" panel on the home page is a static example, not live shell output. It is not generated, so update it by hand whenever files or folders change. The same applies to the status line in the hero metadata.

CSS architecture
css/style.css: design tokens, reset, base styles, layout utilities, background atmosphere.
css/components.css: reusable components. Media queries sit next to the component they affect.

style.css must be loaded before components.css.

Components use role tokens (for example --color-action) instead of raw palette colors, so the color rules live in one place.

Component	Purpose
.system-bar, .nav	Header and navigation
.comment, .tag, .status	Labels and status indicators
.btn	Command-style buttons
.window, .pane	Terminal workspace frames
.hero, .meta	Welcome window and system metadata
.code, .t-*, .cursor	Terminal output, syntax colors, decorative cursor
.section-heading, .pane-grid	Archive overview layout
.status-line	Footer
Design system: Neon Nocturne
Token	Hex	Role
--color-bg	#080B12	Page background
--color-surface	#101725	Windows and panes
--color-surface-raised	#162033	Title bars
--color-cyan → --color-identity	#00F5FF	System identity: brand glyph, pane ids, commands, focus ring
--color-mint → --color-action	#39FFB6	Interaction: links, primary button, active navigation
--color-violet → --color-path	#B47CF9	Directory names in terminal output
--color-magenta → --color-flag	#FF3CAC	Command flags only (rare)
--color-amber → --color-status	#FFB000	Status indicators
--color-text	#F1F5F9	Primary text
--color-text-muted	#94A3B8	Secondary text
--color-border / --color-border-strong	#1E2A3F / #2A3850	Dividers / window frames

Violet is slightly brighter than the original #A855F7 to keep text contrast comfortably above WCAG AA. Glow values are tokens (--glow-*, --ring-focus) and are used only on the brand glyph, focus states, hover states of interactive elements, and the ambient background.

Typography
JetBrains Mono: headings, navigation, commands, identifiers, labels, metadata.
Inter: paragraphs and longer descriptions.

Both are loaded from Google Fonts.

Accessibility notes
Semantic landmarks, skip link, and visible focus states.
Pages that are not linked yet are shown as disabled items, never as broken links.
Decorative glyphs and the cursor are hidden from screen readers; the terminal example has a text description instead.
Status is communicated with a symbol and text, not color alone.
Animations (cursor blink, transitions) are disabled under prefers-reduced-motion.
Running locally

Open the folder in VS Code and start the page with the Live Server extension (right-click index.html → "Open with Live Server").

Roadmap
Foundation (done)
Visual identity (current)
Responsive development
Multi-page architecture
Content integration
Deployment