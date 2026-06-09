# 🚀 GETTING STARTED - SETUP & DEVELOPMENT GUIDE

## 📋 Pre-requisites

Pastikan sudah install:
- **Node.js** (v18.x atau v20.x) → [Download](https://nodejs.org/)
- **Git** → [Download](https://git-scm.com/)
- **npm** atau **yarn** (biasanya bundled dengan Node.js)
- **VS Code** (opsional tapi recommended) → [Download](https://code.visualstudio.com/)

### Verifikasi Installation
```bash
# Check Node.js version (should be v18+)
node --version

# Check npm version (should be v9+)
npm --version

# Check Git version
git --version
```

---

## ⚙️ Pilihan Setup: Tech Stack

Pilih salah satu opsi berikut:

### **Option A: Next.js + Tailwind + Supabase (⭐ RECOMMENDED)**

**Kelebihan:** Modern, Fast, SEO-friendly, Full-stack JavaScript

**Setup Time:** ~30 menit

Lanjut ke [Setup Next.js](#-setup-nextjs--tailwind--supabase)

---

### **Option B: WordPress + Premium Theme**

**Kelebihan:** Easy, CMS-friendly, Mudah maintenance

**Setup Time:** ~1-2 jam

Lihat: [Setup WordPress](#-setup-wordpress)

---

### **Option C: Laravel + Livewire**

**Kelebihan:** Powerful backend, Full customization

**Setup Time:** ~1 jam

Lihat: [Setup Laravel](#-setup-laravel)

---

## 🔧 Setup Next.js + Tailwind + Supabase

### **Step 1: Create Next.js Project**

```bash
# Navigate ke project directory
cd /workspaces/WEB-SMA-NEGERI

# Create Next.js project dengan TypeScript & Tailwind
npx create-next-app@latest . --typescript --tailwind

# Atau manual create:
npx create-next-app@latest web --typescript --tailwind --eslint

# Install dependencies
npm install

# Verify installation
npm run dev
# Visit: http://localhost:3000
```

### **Step 2: Install Required Packages**

```bash
# Supabase & Auth
npm install @supabase/supabase-js @supabase/auth-helpers-nextjs

# UI Components & Utilities
npm install @radix-ui/react-dialog @radix-ui/react-dropdown-menu
npm install class-variance-authority clsx tailwind-merge
npm install zod react-hook-form
npm install lucide-react react-icons

# Data Fetching & State
npm install axios @tanstack/react-query swr

# Animations & Carousel
npm install framer-motion embla-carousel-react embla-carousel-autoplay
npm install aos

# Utilities
npm install date-fns nanoid slugify

# Development
npm install --save-dev prettier eslint @typescript-eslint/eslint-plugin @typescript-eslint/parser
npm install --save-dev jest @testing-library/react @testing-library/jest-dom
```

### **Step 3: Setup Supabase Project**

1. **Go to** [Supabase](https://supabase.com)
2. **Sign up/Login** dengan GitHub atau email
3. **Create New Project:**
   - Organization: Create new or select existing
   - Project name: `SMA Negeri 1 Website`
   - Database password: Generate strong password (save it!)
   - Region: `Southeast Asia (Singapore)` (nearest to Indonesia)
   - Click "Create new project"

4. **Wait** untuk project initialization (5-10 menit)

5. **Get your credentials:**
   - Go to **Settings → API**
   - Copy **URL** dan **Anon Key**
   - Save untuk `.env.local`

### **Step 4: Configure Environment Variables**

```bash
# Create file: .env.local
cat > .env.local << 'EOF'
NEXT_PUBLIC_SUPABASE_URL=YOUR_SUPABASE_URL
NEXT_PUBLIC_SUPABASE_ANON_KEY=YOUR_ANON_KEY
SUPABASE_SERVICE_ROLE_KEY=YOUR_SERVICE_ROLE_KEY
EOF

# Edit dengan nilai real dari Supabase
# JANGAN PUSH FILE INI KE GIT!
```

### **Step 5: Create Database Schema**

Login ke Supabase → Go to **SQL Editor** → Create new query → Paste:

```sql
-- Dari file: TECH-STACK.md (Database Schema section)
-- Copy seluruh SQL schema dan execute
```

### **Step 6: Test Setup**

```bash
# Start development server
npm run dev

# Test di browser
# http://localhost:3000

# Ctrl+C untuk stop server
```

---

## 📁 Project Structure Setup

```bash
# Create folder structure
mkdir -p app components lib public/images public/documents styles
mkdir -p __tests__ migrations

# Create essential files
touch middleware.ts tailwind.config.js tsconfig.json

# Initialize git (jika belum)
git init
git add .
git commit -m "Initial commit: Next.js boilerplate"
```

---

## 🧪 Test Your Development Environment

Buat file test untuk memastikan semua working:

```bash
# Create: app/page.tsx
cat > app/page.tsx << 'EOF'
export default function Home() {
  return (
    <div className="flex items-center justify-center min-h-screen">
      <h1 className="text-4xl font-bold text-blue-600">
        ✅ Next.js Setup Success!
      </h1>
    </div>
  )
}
EOF

# Run development server
npm run dev
```

Akses `http://localhost:3000` dan Anda harus melihat pesan sukses.

---

## 🔧 Setup WordPress

### **Option B: WordPress Local Development**

Jika prefer WordPress daripada Next.js:

#### **Local Setup dengan LocalWP**

1. **Download** [LocalWP](https://localwp.com/)
2. **Install** dan buat site baru
3. **Install Theme**: OceanWP atau Hello Elementor
4. **Install Plugins**:
   - Elementor Pro (untuk page builder)
   - WPForms Pro (forms)
   - Yoast SEO Premium
   - LearnDash (LMS)
   - Wordfence Security

#### **Hosting Recommendation**
- [Cloudways](https://cloudways.com) - Managed cloud hosting
- [SiteGround](https://www.siteground.com) - Reliable WordPress hosting
- [Kinsta](https://kinsta.com) - Premium managed hosting

#### **Setup Time**: 1-2 jam
#### **Maintenance**: Mudah (GUI-based)

---

## 🔧 Setup Laravel

### **Option C: Laravel Development**

```bash
# Create Laravel project
composer create-project laravel/laravel sma-negeri

# Navigate to project
cd sma-negeri

# Install Livewire & Filament (Admin Panel)
composer require livewire/livewire
composer require filament/filament

# Run migrations
php artisan migrate

# Start development server
php artisan serve
# Visit: http://localhost:8000
```

---

## 📝 Common Commands Reference

### **Next.js Development**
```bash
npm run dev         # Start dev server
npm run build       # Build for production
npm run start       # Start production server
npm run lint        # Run linter
npm run type-check  # Type checking
npm test            # Run tests
```

### **Database Migration (Supabase)**
```bash
# Create migration file
supabase migration new create_users_table

# Run migration
supabase db push

# Reset database
supabase db reset
```

### **Git Workflow**
```bash
# Create feature branch
git checkout -b feature/hero-section

# Add changes
git add .

# Commit dengan message
git commit -m "feat: add hero section component"

# Push ke remote
git push origin feature/hero-section

# Create Pull Request di GitHub
```

---

## 🐛 Troubleshooting

### **Error: Port 3000 already in use**
```bash
# Kill process on port 3000
lsof -i :3000
kill -9 <PID>

# Or use different port
npm run dev -- -p 3001
```

### **Error: Module not found**
```bash
# Clear node_modules & reinstall
rm -rf node_modules package-lock.json
npm install
```

### **Error: Supabase connection failed**
```bash
# Check .env.local file
cat .env.local

# Verify URL & API key dari Supabase dashboard
# Restart dev server
npm run dev
```

### **TypeScript errors**
```bash
# Run type checker
npm run type-check

# Fix TypeScript errors before committing
```

---

## 📚 Next Steps (After Setup)

1. **Read Documentation**
   - BLUEPRINT.md → Understand requirements
   - TECH-STACK.md → Know the tech
   - DESIGN-GUIDE.md → Learn design system
   - ROADMAP.md → See timeline

2. **Create Components**
   - Start dengan atomic design
   - Build Button, Input, Card, etc
   - Move to complex components (Navbar, Hero)

3. **Setup Database**
   - Run SQL migrations
   - Create API routes
   - Test CRUD operations

4. **Start Coding**
   - Begin with Phase 1 (Foundation)
   - Follow ROADMAP.md timeline
   - Push to GitHub regularly

---

## 🚀 Ready for Development!

Setelah setup selesai, lanjut dengan:

1. **Create Navbar Component** → `components/Navbar.tsx`
2. **Create Hero Section** → `components/Hero.tsx`
3. **Setup Layout** → `app/layout.tsx`
4. **Create Homepage** → `app/page.tsx`

Lihat file **IMPLEMENTATION-GUIDE.md** untuk detail coding.

---

## 📖 Useful Resources

### **Next.js**
- [Next.js Documentation](https://nextjs.org/docs)
- [Next.js Tutorial](https://nextjs.org/learn)

### **Tailwind CSS**
- [Tailwind CSS Docs](https://tailwindcss.com/docs)
- [Tailwind UI Components](https://tailwindui.com)

### **Supabase**
- [Supabase Docs](https://supabase.com/docs)
- [Supabase Auth Guide](https://supabase.com/docs/guides/auth)

### **React**
- [React Documentation](https://react.dev)
- [React Patterns](https://react-patterns.com)

### **TypeScript**
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [TypeScript Deep Dive](https://basarat.gitbook.io/typescript/)

---

## ✅ Development Environment Checklist

Pastikan semua sudah selesai:

- [ ] Node.js v18+ installed
- [ ] Git installed & configured
- [ ] Next.js project created
- [ ] All npm packages installed
- [ ] .env.local configured with Supabase keys
- [ ] Database schema created in Supabase
- [ ] Development server running (npm run dev)
- [ ] Can access http://localhost:3000
- [ ] TypeScript & ESLint working
- [ ] Ready to start coding! 🎉

---

**Status:** ✅ Getting Started Guide Complete

*Mulai development di [IMPLEMENTATION-GUIDE.md](./IMPLEMENTATION-GUIDE.md) setelah setup selesai.*
