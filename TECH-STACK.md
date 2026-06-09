# 🛠️ TECH STACK DETAIL - Next.js + Tailwind CSS + Supabase

## 📦 Dependencies & Packages

### **Frontend (Next.js 14+)**
```json
{
  "dependencies": {
    "next": "^14.0.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "typescript": "^5.0.0",
    
    // Styling
    "tailwindcss": "^3.3.0",
    "autoprefixer": "^10.4.0",
    "postcss": "^8.4.0",
    "@tailwindcss/forms": "^0.5.0",
    "@tailwindcss/typography": "^0.5.0",
    "lucide-react": "^0.263.0",
    
    // UI Components
    "@radix-ui/react-dialog": "^1.1.0",
    "@radix-ui/react-dropdown-menu": "^2.0.0",
    "@radix-ui/react-slot": "^2.0.0",
    "class-variance-authority": "^0.7.0",
    "clsx": "^2.0.0",
    "tailwind-merge": "^2.0.0",
    "zod": "^3.22.0",
    "react-hook-form": "^7.45.0",
    
    // Database & Auth
    "@supabase/supabase-js": "^2.37.0",
    "@supabase/auth-helpers-nextjs": "^0.7.0",
    
    // API & Data Fetching
    "axios": "^1.5.0",
    "@tanstack/react-query": "^5.0.0",
    "swr": "^2.2.0",
    
    // Carousel & Slider
    "embla-carousel-react": "^7.0.0",
    "embla-carousel-autoplay": "^7.0.0",
    
    // Animations
    "framer-motion": "^10.16.0",
    "aos": "^2.3.4",
    
    // Icons & Images
    "react-icons": "^4.11.0",
    "next-image-export-optimizer": "^1.8.0",
    
    // Utilities
    "date-fns": "^2.30.0",
    "nanoid": "^4.0.2",
    "slugify": "^1.6.6"
  },
  "devDependencies": {
    "@types/node": "^20.0.0",
    "@types/react": "^18.2.0",
    "@types/react-dom": "^18.2.0",
    "eslint": "^8.0.0",
    "eslint-config-next": "^14.0.0",
    "prettier": "^3.0.0",
    "@typescript-eslint/eslint-plugin": "^6.0.0",
    "@typescript-eslint/parser": "^6.0.0",
    "jest": "^29.0.0",
    "@testing-library/react": "^14.0.0",
    "@testing-library/jest-dom": "^6.0.0"
  }
}
```

---

## 🗄️ Database Schema (Supabase PostgreSQL)

```sql
-- Enable UUID extension
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

-- ===== USERS TABLE =====
CREATE TABLE public.users (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  email VARCHAR(255) UNIQUE NOT NULL,
  password_hash VARCHAR(255),
  full_name VARCHAR(255) NOT NULL,
  role VARCHAR(50) NOT NULL DEFAULT 'user',
  -- Roles: 'super_admin', 'editor', 'teacher', 'principal', 'user'
  avatar_url VARCHAR(500),
  is_active BOOLEAN DEFAULT TRUE,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  
  CONSTRAINT valid_role CHECK (role IN ('super_admin', 'editor', 'teacher', 'principal', 'user'))
);

-- ===== NEWS & ANNOUNCEMENTS TABLE =====
CREATE TABLE public.news (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  title VARCHAR(255) NOT NULL,
  slug VARCHAR(255) UNIQUE NOT NULL,
  content TEXT NOT NULL,
  category VARCHAR(50) NOT NULL,
  -- Categories: 'akademik', 'kegiatan', 'pengumuman', 'prestasi'
  featured_image VARCHAR(500),
  excerpt VARCHAR(500),
  author_id UUID NOT NULL REFERENCES public.users(id) ON DELETE SET NULL,
  is_published BOOLEAN DEFAULT FALSE,
  is_featured BOOLEAN DEFAULT FALSE,
  published_at TIMESTAMP WITH TIME ZONE,
  scheduled_at TIMESTAMP WITH TIME ZONE,
  views_count INTEGER DEFAULT 0,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
);

-- ===== GALLERIES TABLE =====
CREATE TABLE public.galleries (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  title VARCHAR(255) NOT NULL,
  description TEXT,
  images JSONB NOT NULL, -- Array of {url, alt, caption}
  category VARCHAR(100),
  created_by UUID NOT NULL REFERENCES public.users(id),
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
);

-- ===== DOCUMENTS TABLE =====
CREATE TABLE public.documents (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  title VARCHAR(255) NOT NULL,
  description TEXT,
  file_url VARCHAR(500) NOT NULL,
  file_type VARCHAR(50), -- pdf, docx, xlsx, etc
  category VARCHAR(100), -- modul, surat, panduan, dll
  is_public BOOLEAN DEFAULT TRUE,
  uploaded_by UUID NOT NULL REFERENCES public.users(id),
  downloads_count INTEGER DEFAULT 0,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
);

-- ===== CONTACT MESSAGES TABLE =====
CREATE TABLE public.contact_messages (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  name VARCHAR(255) NOT NULL,
  email VARCHAR(255) NOT NULL,
  phone VARCHAR(20),
  subject VARCHAR(255) NOT NULL,
  message TEXT NOT NULL,
  is_read BOOLEAN DEFAULT FALSE,
  is_replied BOOLEAN DEFAULT FALSE,
  replied_message TEXT,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
);

-- ===== SETTINGS TABLE =====
CREATE TABLE public.settings (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  setting_key VARCHAR(100) UNIQUE NOT NULL,
  setting_value TEXT,
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
);

-- ===== INDEXES =====
CREATE INDEX idx_news_published ON public.news(is_published, published_at DESC);
CREATE INDEX idx_news_category ON public.news(category);
CREATE INDEX idx_news_author ON public.news(author_id);
CREATE INDEX idx_users_email ON public.users(email);
CREATE INDEX idx_documents_category ON public.documents(category);
CREATE INDEX idx_galleries_category ON public.galleries(category);
CREATE INDEX idx_contact_messages_created ON public.contact_messages(created_at DESC);

-- ===== INITIAL SETTINGS =====
INSERT INTO public.settings (setting_key, setting_value) VALUES
  ('school_name', 'SMA Negeri 1'),
  ('school_email', 'info@smanegeri1.sch.id'),
  ('school_phone', '+62-xxx-xxxxxx'),
  ('school_address', 'Jln. Pendidikan No. 1'),
  ('school_city', 'Kota'),
  ('school_province', 'Provinsi'),
  ('principal_greeting', 'Selamat datang di SMA Negeri 1'),
  ('maintenance_mode', 'false'),
  ('dark_mode_enabled', 'true'),
  ('analytics_enabled', 'true');
```

---

## 🔐 Authentication & Authorization

### **Next.js Auth Configuration**
```typescript
// lib/auth.ts
import { createServerComponentClient } from '@supabase/auth-helpers-nextjs'
import { cookies } from 'next/headers'

export const createClient = () =>
  createServerComponentClient({ cookies })

export type UserRole = 'super_admin' | 'editor' | 'teacher' | 'principal' | 'user'

export async function getCurrentUser() {
  const supabase = createClient()
  const { data: { session } } = await supabase.auth.getSession()
  
  if (!session) return null
  
  const { data: user } = await supabase
    .from('users')
    .select('*')
    .eq('id', session.user.id)
    .single()
  
  return user
}

export function canAccess(userRole: UserRole, requiredRole: UserRole[]) {
  return requiredRole.includes(userRole)
}
```

### **Role-Based Access Control (RBAC)**
```typescript
// middleware.ts
import { NextRequest, NextResponse } from 'next/server'

export async function middleware(request: NextRequest) {
  const token = request.cookies.get('auth-token')?.value
  
  // Public pages (akses semua)
  const publicPages = ['/', '/profil', '/akademik', '/kesiswaan', '/ppdb', '/kontak']
  
  // Admin pages (require login)
  const adminPages = ['/admin']
  
  const path = request.nextUrl.pathname
  
  if (adminPages.some(p => path.startsWith(p)) && !token) {
    return NextResponse.redirect(new URL('/login', request.url))
  }
  
  return NextResponse.next()
}

export const config = {
  matcher: ['/((?!api|_next/static|_next/image|favicon.ico).*)']
}
```

---

## 🚀 API Endpoints

### **News & Announcements**
```
GET    /api/news                    # Ambil semua berita
GET    /api/news/:id               # Ambil berita detail
POST   /api/news                   # Buat berita (admin)
PUT    /api/news/:id               # Update berita (admin)
DELETE /api/news/:id               # Hapus berita (admin)
GET    /api/news/featured          # Ambil berita featured
GET    /api/news/category/:cat     # Ambil berita by kategori
```

### **Users & Auth**
```
POST   /api/auth/register          # Register pengguna
POST   /api/auth/login             # Login
POST   /api/auth/logout            # Logout
GET    /api/auth/me                # Ambil current user
POST   /api/auth/refresh           # Refresh token
GET    /api/users                  # Ambil daftar pengguna (admin)
PUT    /api/users/:id              # Update user (admin)
DELETE /api/users/:id              # Hapus user (admin)
```

### **Galleries**
```
GET    /api/galleries              # Ambil semua galeri
POST   /api/galleries              # Buat galeri (admin)
PUT    /api/galleries/:id          # Update galeri
DELETE /api/galleries/:id          # Hapus galeri
POST   /api/galleries/:id/upload   # Upload gambar
```

### **Documents**
```
GET    /api/documents              # Ambil dokumen
GET    /api/documents/:id/download # Download dokumen
POST   /api/documents              # Upload dokumen (admin)
DELETE /api/documents/:id          # Hapus dokumen
```

### **Contact**
```
POST   /api/contact                # Submit form kontak
GET    /api/contact                # Ambil pesan kontak (admin)
PUT    /api/contact/:id            # Update pesan
DELETE /api/contact/:id            # Hapus pesan
```

---

## 🎨 Component Architecture

### **Atomic Design Pattern**
```
atoms/           # Komponen kecil (Button, Input, Badge)
  ├── Button.tsx
  ├── Input.tsx
  ├── Badge.tsx
  └── ...

molecules/       # Kombinasi atoms (SearchBox, NewsCard)
  ├── NewsCard.tsx
  ├── SearchBox.tsx
  ├── AuthForm.tsx
  └── ...

organisms/       # Kombinasi molecules (Header, Hero)
  ├── Navbar.tsx
  ├── Footer.tsx
  ├── Hero.tsx
  ├── NewsGrid.tsx
  └── ...

templates/       # Layout templates
  ├── PageTemplate.tsx
  ├── AdminTemplate.tsx
  └── ...
```

---

## 🧪 Testing Strategy

### **Unit Tests (Jest + React Testing Library)**
```typescript
// __tests__/components/Button.test.tsx
import { render, screen } from '@testing-library/react'
import userEvent from '@testing-library/user-event'
import Button from '@/components/Button'

describe('Button Component', () => {
  it('renders button with text', () => {
    render(<Button>Click me</Button>)
    expect(screen.getByRole('button')).toBeInTheDocument()
  })
  
  it('handles click event', async () => {
    const handleClick = jest.fn()
    render(<Button onClick={handleClick}>Click</Button>)
    
    await userEvent.click(screen.getByRole('button'))
    expect(handleClick).toHaveBeenCalledTimes(1)
  })
})
```

### **Integration Tests**
```typescript
// __tests__/api/news.test.ts
import { GET } from '@/app/api/news/route'

describe('News API', () => {
  it('returns list of news', async () => {
    const response = await GET()
    const data = await response.json()
    
    expect(response.status).toBe(200)
    expect(Array.isArray(data)).toBe(true)
  })
})
```

---

## 📊 Performance Optimization

### **Next.js Optimizations**
1. **Image Optimization**
   - Gunakan `next/image` component
   - Automatic format conversion (WebP, AVIF)
   - Lazy loading by default

2. **Code Splitting**
   - Dynamic imports untuk route-based splitting
   - `next/dynamic` untuk component lazy loading

3. **Font Optimization**
   - Self-hosted Google Fonts
   - Font subsetting

4. **Caching Strategy**
   - Static pages: ISR (Incremental Static Regeneration)
   - Dynamic pages: SWR + Redis
   - API response caching

### **Tailwind CSS Optimization**
```typescript
// tailwind.config.js
module.exports = {
  content: [
    './app/**/*.{js,ts,jsx,tsx}',
    './components/**/*.{js,ts,jsx,tsx}',
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

---

## 🔒 Security Best Practices

1. **Environment Variables**
   ```
   NEXT_PUBLIC_SUPABASE_URL
   NEXT_PUBLIC_SUPABASE_ANON_KEY
   SUPABASE_SERVICE_ROLE_KEY (secret)
   ```

2. **Input Validation**
   - Zod untuk schema validation
   - Server-side validation mandatory

3. **CORS & CSRF**
   - Configure CORS headers
   - CSRF token di forms

4. **Rate Limiting**
   - Implement di API routes
   - Gunakan middleware

5. **Password Security**
   - Bcrypt hashing (Supabase Auth handle ini)
   - 2FA support

---

## 🚢 Deployment Checklist

- [ ] Environment variables configured
- [ ] Database migrations completed
- [ ] Tests passing (95%+ coverage)
- [ ] Lighthouse score 90+
- [ ] SEO meta tags configured
- [ ] Analytics setup
- [ ] Email service configured
- [ ] SSL/HTTPS enabled
- [ ] Backup strategy in place
- [ ] Monitoring & alerting setup
- [ ] Documentation updated
- [ ] Deployment guide ready

---

## 📚 Referensi & Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [Tailwind CSS Docs](https://tailwindcss.com/docs)
- [Supabase Docs](https://supabase.com/docs)
- [React Query Docs](https://tanstack.com/query/latest)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [Web Accessibility (WCAG)](https://www.w3.org/WAI/WCAG21/quickref/)

---

**Status:** ✅ Tech Stack Detail Selesai

*Siap untuk setup project!*
