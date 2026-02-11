# NutriSync - Design Documentation

## Table of Contents
1. [Design Philosophy](#design-philosophy)
2. [Visual Design System](#visual-design-system)
3. [Component Architecture](#component-architecture)
4. [User Interface Design](#user-interface-design)
5. [User Experience (UX) Design](#user-experience-ux-design)
6. [Responsive Design](#responsive-design)
7. [Animation & Interactions](#animation--interactions)
8. [Accessibility](#accessibility)
9. [Design Patterns](#design-patterns)

---

## Design Philosophy

### Core Principles
- **Clarity**: Clean, uncluttered interfaces that prioritize content and functionality
- **Consistency**: Unified design language across all components and pages
- **Accessibility**: Inclusive design that works for all users
- **Performance**: Smooth animations and fast interactions
- **Responsiveness**: Seamless experience across all device sizes

### Design Goals
- Create a calming, health-focused aesthetic
- Make complex health data easy to understand
- Encourage daily engagement through delightful interactions
- Build trust through professional, polished design

---

## Visual Design System

### Color Palette

#### Primary Colors
- **Background**: Dynamic based on theme (light/dark mode support)
- **Foreground**: High contrast text colors
- **Primary**: Brand accent color for CTAs and highlights
- **Secondary**: Supporting color for less prominent elements
- **Muted**: Subtle backgrounds and borders

#### Semantic Colors
- **Success**: Green tones for positive feedback and achievements
- **Warning**: Yellow/orange for cautions and alerts
- **Destructive**: Red for errors and critical actions
- **Info**: Blue for informational messages

#### Theme Support
- Light mode with soft, clean backgrounds
- Dark mode with comfortable, eye-friendly colors
- Automatic theme detection via `next-themes`
- Smooth theme transitions

### Typography

#### Font System
- **Primary Font**: System font stack for optimal performance
- **Font Sizes**: Responsive scale from xs to 4xl
- **Font Weights**: 400 (normal), 500 (medium), 600 (semibold), 700 (bold)
- **Line Heights**: Optimized for readability (1.5 for body, 1.2 for headings)

#### Text Hierarchy
```
- Headings: h1 (2xl-4xl), h2 (xl-2xl), h3 (lg-xl)
- Body: base (16px equivalent)
- Small: sm (14px equivalent)
- Tiny: xs (12px equivalent)
```

### Spacing System
- Base unit: 4px (0.25rem)
- Scale: 0, 1, 2, 3, 4, 5, 6, 8, 10, 12, 16, 20, 24, 32, 40, 48, 64
- Consistent padding and margins across components
- Container max-width: 1200px for optimal readability

### Border & Radius
- **Border Width**: 1px standard, 2px for emphasis
- **Border Radius**: 
  - sm: 0.25rem (buttons, inputs)
  - md: 0.5rem (cards, dialogs)
  - lg: 0.75rem (large containers)
  - full: 9999px (pills, avatars)

### Shadows & Elevation
- **sm**: Subtle shadow for slight elevation
- **md**: Standard card shadow
- **lg**: Modal and dropdown shadow
- **xl**: Maximum elevation for overlays

---

## Component Architecture

### Design System Components (Shadcn UI)

#### Layout Components
- **Sidebar**: Collapsible navigation with rail
- **SidebarProvider**: Context for sidebar state
- **SidebarInset**: Main content area with sidebar
- **Card**: Container for grouped content
- **Separator**: Visual dividers

#### Form Components
- **Input**: Text input with validation states
- **Textarea**: Multi-line text input
- **Select**: Dropdown selection
- **Checkbox**: Boolean selection
- **Radio Group**: Single choice from multiple options
- **Switch**: Toggle control
- **Slider**: Range input
- **Form**: Form wrapper with validation (React Hook Form + Zod)

#### Feedback Components
- **Toast**: Temporary notifications
- **Sonner**: Advanced toast notifications
- **Alert**: Persistent messages
- **Alert Dialog**: Confirmation dialogs
- **Progress**: Progress indicators
- **Skeleton**: Loading placeholders

#### Navigation Components
- **Tabs**: Content organization
- **Accordion**: Expandable sections
- **Breadcrumb**: Navigation trail
- **Navigation Menu**: Complex navigation structures
- **Dropdown Menu**: Contextual actions
- **Context Menu**: Right-click menus

#### Data Display Components
- **Table**: Structured data display
- **Badge**: Status indicators
- **Avatar**: User representation
- **Tooltip**: Contextual help
- **Hover Card**: Rich hover information
- **Chart**: Data visualization (Recharts integration)

#### Overlay Components
- **Dialog**: Modal windows
- **Sheet**: Side panels
- **Popover**: Floating content
- **Drawer**: Mobile-friendly overlays

### Custom Application Components

#### Core Components
```
Navbar
├── Logo and branding
├── Navigation links
├── Authentication controls
└── Mobile menu toggle

AppSidebar
├── User profile section
├── Navigation menu
├── Quick actions
└── Collapse/expand control

Layout
├── Navbar (fixed top)
├── Sidebar (conditional, authenticated users)
├── Main content area
└── Footer
```

#### Feature Components
```
Dashboard
├── WelcomeMessage
├── WeightTracker
├── ProgressTracker
├── NutritionGoals
└── MealRecommendations

Calculator
├── UserForm (BMI/BMR inputs)
└── ResultCard (calculations display)

AiNutriScan
├── Image upload interface
├── AI analysis display
└── Nutritional breakdown

AiMealPlanner
├── Preference inputs
├── AI meal generation
└── Meal cards display
```

---

## User Interface Design

### Page Layouts

#### Landing Page (Index)
```
┌─────────────────────────────────┐
│         Navbar                  │
├─────────────────────────────────┤
│         Hero Section            │
│    (CTA + Demo Video)           │
├─────────────────────────────────┤
│      Features Section           │
│    (Grid of capabilities)       │
├─────────────────────────────────┤
│         Footer                  │
└─────────────────────────────────┘
```

#### Dashboard Layout
```
┌─────────────────────────────────┐
│         Navbar                  │
├──────┬──────────────────────────┤
│      │  Welcome Message         │
│ Side │                          │
│ bar  ├──────────┬───────────────┤
│      │  Weight  │   Progress    │
│      │ Tracker  │   Tracker     │
│      ├──────────┼───────────────┤
│      │Nutrition │     Meal      │
│      │  Goals   │Recommendations│
└──────┴──────────┴───────────────┘
```

#### Calculator Page
```
┌─────────────────────────────────┐
│         Navbar                  │
├──────┬──────────────────────────┤
│      │                          │
│ Side │     User Input Form      │
│ bar  │   (Height, Weight, etc)  │
│      │                          │
│      ├──────────────────────────┤
│      │     Results Display      │
│      │   (BMI, BMR, Calories)   │
└──────┴──────────────────────────┘
```

#### AI NutriScan Page
```
┌─────────────────────────────────┐
│         Navbar                  │
├─────────────────────────────────┤
│                                 │
│      Image Upload Area          │
│    (Drag & Drop / Click)        │
│                                 │
├─────────────────────────────────┤
│    AI Analysis Results          │
│  (Dish Name + Nutrition Info)   │
└─────────────────────────────────┘
```

### Component Design Specifications

#### Card Design
- Background: Subtle card background
- Border: 1px solid border color
- Radius: 0.5rem
- Padding: 1.5rem (24px)
- Shadow: Subtle elevation
- Hover: Slight shadow increase (interactive cards)

#### Button Design
- **Primary**: Solid background, high contrast
- **Secondary**: Outlined with border
- **Ghost**: Transparent with hover state
- **Destructive**: Red for dangerous actions
- Sizes: sm (32px), default (40px), lg (48px)
- States: default, hover, active, disabled, loading

#### Input Design
- Height: 40px (default)
- Border: 1px solid with focus ring
- Radius: 0.375rem
- Padding: 0.5rem 0.75rem
- States: default, focus, error, disabled
- Label: Above input, 14px, medium weight

#### Navigation Design
- **Desktop**: Horizontal menu in navbar
- **Mobile**: Hamburger menu with slide-in panel
- Active state: Highlighted with primary color
- Hover: Subtle color transition
- Icons: 16px, aligned with text

---

## User Experience (UX) Design

### User Flows

#### New User Onboarding
```
1. Landing Page
   ↓
2. Register Account
   ↓
3. Login
   ↓
4. Calculator (Enter Body Metrics)
   ↓
5. Dashboard (View Personalized Data)
```

#### Daily Usage Flow
```
1. Login
   ↓
2. Dashboard (Overview)
   ↓
3. Log Weight (if needed)
   ↓
4. Scan Food (AI NutriScan)
   ↓
5. View Nutrition Progress
   ↓
6. Get Meal Recommendations
```

#### Food Analysis Flow
```
1. Navigate to AI NutriScan
   ↓
2. Upload Food Image
   ↓
3. AI Processing (Loading State)
   ↓
4. View Nutritional Analysis
   ↓
5. Save to Log (optional)
```

### Interaction Patterns

#### Loading States
- Skeleton screens for content loading
- Spinner for button actions
- Progress bar for file uploads
- Shimmer effect for placeholders

#### Empty States
- Friendly illustrations
- Clear call-to-action
- Helpful guidance text
- Example data or tutorials

#### Error States
- Clear error messages
- Suggested actions
- Retry mechanisms
- Fallback content

#### Success States
- Toast notifications
- Visual confirmation
- Smooth transitions
- Positive feedback

### Micro-interactions
- Button press animations
- Input focus effects
- Card hover elevations
- Smooth page transitions
- Progress animations
- Chart data animations

---

## Responsive Design

### Breakpoints
```css
sm: 640px   /* Mobile landscape */
md: 768px   /* Tablet */
lg: 1024px  /* Desktop */
xl: 1280px  /* Large desktop */
2xl: 1536px /* Extra large */
```

### Mobile-First Approach
- Base styles for mobile (320px+)
- Progressive enhancement for larger screens
- Touch-friendly targets (min 44x44px)
- Simplified navigation on mobile
- Optimized images and assets

### Responsive Patterns

#### Grid Layouts
```
Mobile:    1 column
Tablet:    2 columns
Desktop:   3-4 columns
```

#### Dashboard Grid
```
Mobile:    Stack vertically
Tablet:    2x2 grid
Desktop:   Complex grid (4 cols, 8 cols)
```

#### Navigation
```
Mobile:    Hamburger menu
Tablet:    Horizontal menu
Desktop:   Full navigation + sidebar
```

### Touch Optimization
- Larger tap targets on mobile
- Swipe gestures for carousels
- Pull-to-refresh (where applicable)
- Bottom navigation for key actions
- Thumb-friendly zones

---

## Animation & Interactions

### Animation Library
- **Framer Motion**: Primary animation library
- **Tailwind Animate**: CSS-based animations
- **Recharts**: Chart animations

### Animation Principles
- **Duration**: 200-300ms for micro-interactions, 300-500ms for page transitions
- **Easing**: Smooth, natural curves (ease-in-out)
- **Purpose**: Enhance understanding, not distract
- **Performance**: GPU-accelerated transforms

### Key Animations

#### Page Transitions
```typescript
initial={{ opacity: 0, y: 10 }}
animate={{ opacity: 1, y: 0 }}
exit={{ opacity: 0, y: -10 }}
transition={{ duration: 0.3 }}
```

#### Navbar Entry
```typescript
initial={{ y: -20, opacity: 0 }}
animate={{ y: 0, opacity: 1 }}
transition={{ duration: 0.5 }}
```

#### Card Hover
```css
transition: shadow 200ms ease-in-out
hover: shadow-lg
```

#### Button Press
```css
active: scale-95
transition: transform 100ms
```

#### Chart Animations
- Smooth data entry animations
- Hover tooltips with fade-in
- Legend interactions
- Responsive resize transitions

---

## Accessibility

### WCAG Compliance Goals
- Target: WCAG 2.1 Level AA
- Color contrast ratios: 4.5:1 (text), 3:1 (UI components)
- Keyboard navigation support
- Screen reader compatibility

### Accessibility Features

#### Semantic HTML
- Proper heading hierarchy (h1 → h6)
- Semantic elements (nav, main, footer, article)
- ARIA labels where needed
- Form labels and descriptions

#### Keyboard Navigation
- Tab order follows visual flow
- Focus indicators visible
- Skip links for main content
- Escape key closes modals
- Arrow keys for menus

#### Screen Reader Support
- Alt text for images
- ARIA labels for icons
- Live regions for dynamic content
- Descriptive link text
- Form error announcements

#### Visual Accessibility
- High contrast mode support
- Scalable text (rem units)
- No information by color alone
- Focus indicators
- Reduced motion support

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## Design Patterns

### State Management Patterns

#### Loading Pattern
```tsx
{loading && <Skeleton />}
{!loading && data && <Content />}
{!loading && !data && <EmptyState />}
```

#### Error Boundary Pattern
```tsx
{error && <Alert variant="destructive">{error}</Alert>}
{!error && <Content />}
```

#### Protected Route Pattern
```tsx
<ProtectedRoute>
  <Dashboard />
</ProtectedRoute>
```

### Form Patterns

#### Validation Pattern
- Real-time validation with Zod
- Error messages below inputs
- Success indicators
- Disabled submit until valid

#### Multi-step Form Pattern
- Progress indicator
- Back/Next navigation
- Save draft capability
- Summary before submit

### Data Display Patterns

#### Card Grid Pattern
```tsx
<div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
  {items.map(item => <Card key={item.id} />)}
</div>
```

#### Dashboard Widget Pattern
- Consistent card styling
- Header with title and actions
- Content area with data
- Footer with additional info

#### Chart Pattern
- Responsive container
- Legend and tooltips
- Loading state
- Empty state with message

### Navigation Patterns

#### Breadcrumb Pattern
- Show current location
- Clickable ancestors
- Separator icons
- Truncate on mobile

#### Tab Pattern
- Clear active state
- Keyboard navigation
- Content lazy loading
- URL synchronization

### Feedback Patterns

#### Toast Notification Pattern
- Auto-dismiss (3-5 seconds)
- Action buttons (undo, view)
- Stack multiple toasts
- Position: bottom-right

#### Confirmation Dialog Pattern
- Clear question
- Destructive action highlighted
- Cancel as default
- Keyboard shortcuts (Enter/Esc)

---

## Design Tools & Resources

### Design System
- **Component Library**: Shadcn UI (Radix UI primitives)
- **Styling**: Tailwind CSS
- **Icons**: Lucide React
- **Animations**: Framer Motion

### Development Tools
- **TypeScript**: Type-safe component props
- **Vite**: Fast development and builds
- **ESLint**: Code quality
- **Prettier**: Code formatting (recommended)

### Design Tokens
All design tokens are managed through Tailwind configuration:
- Colors: `tailwind.config.ts`
- Spacing: Tailwind default scale
- Typography: Tailwind default scale
- Shadows: Tailwind default scale

### Component Documentation
- Shadcn UI docs: https://ui.shadcn.com
- Radix UI docs: https://www.radix-ui.com
- Tailwind CSS docs: https://tailwindcss.com

---

## Future Design Considerations

### Planned Enhancements
- Dark mode refinements
- Custom theme builder
- Advanced data visualizations
- Gamification elements (badges, streaks)
- Social features UI
- Mobile app design (React Native)
- Accessibility audit and improvements
- Performance optimizations
- Animation polish
- Micro-interaction refinements

### Design Debt
- Standardize spacing across all components
- Create comprehensive style guide
- Document all component variants
- Establish icon usage guidelines
- Define illustration style
- Create loading state library
- Build error state library
- Develop empty state library

---

## Conclusion

This design system provides a solid foundation for NutriSync's user interface. It emphasizes clarity, consistency, and accessibility while maintaining flexibility for future enhancements. All components are built with reusability and maintainability in mind, ensuring a scalable design system that can grow with the application.
