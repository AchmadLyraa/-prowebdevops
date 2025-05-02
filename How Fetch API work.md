Saya akan menjelaskan secara sederhana tentang penggunaan fetch API di project Next.js ini, seperti mengajarkan anak SD.

## Lokasi API dan Keterhubungannya

Berdasarkan struktur folder yang Anda tunjukkan:

### 1. Folder Utama untuk API:
```
src/services/api/
```

Folder ini adalah "rumah" untuk semua kode yang berhubungan dengan API. Di dalam folder ini ada:

- `config.ts` - Berisi konfigurasi dasar API (URL, header, dll.)
- `index.ts` - Mengekspor semua fungsi API agar mudah digunakan
- `auth.ts` - Berisi fungsi-fungsi untuk login, register, logout
- `loyalty.ts` - Berisi fungsi-fungsi untuk sistem poin loyalty

### 2. Cara Kerjanya:

Bayangkan API seperti surat. Kita perlu:
1. Menulis surat (menyiapkan request)
2. Mengirim surat (melakukan fetch)
3. Membaca balasannya (mendapatkan response)

Mari lihat contoh alur penggunaan API:

```
[Halaman Sign-in] → [useAuth hook] → [AuthContext] → [API service] → [Server]
```

### 3. Penjelasan Simpel:

- **Halaman**: Tombol "Sign In" ditekan
- **Hook**: `useAuth` dipanggil
- **Context**: `AuthContext` menyimpan data user setelah login
- **Service**: `auth.ts` mengirim data ke server dengan fetch
- **Server**: Memproses dan memberi jawaban

### 4. Contoh Kode:

#### `src/services/api/auth.ts`:
```typescript
// Fungsi login yang mengirim data ke server
export const loginUser = async (email: string, password: string) => {
  const response = await fetch('https://api-example.com/login', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({ email, password })
  });
  
  if (!response.ok) {
    throw new Error('Login failed');
  }
  
  return await response.json();
};
```

#### `src/contexts/AuthContext.tsx`:
```typescript
import { loginUser } from '@/services/api/auth';

// Fungsi login dalam context
const login = async (email, password) => {
  setIsLoading(true);
  try {
    const userData = await loginUser(email, password);
    setUser(userData);
    setError(null);
  } catch (error) {
    setError('Login failed. Please check your credentials.');
  } finally {
    setIsLoading(false);
  }
};
```

#### `src/hooks/useAuth.ts`:
```typescript
// Hook untuk menggunakan context
export const useAuth = () => {
  const context = useContext(AuthContext);
  if (!context) {
    throw new Error('useAuth must be used within AuthProvider');
  }
  return context; // Berisi login, user, isLoading, error
};
```

## Penjelasan Fungsi Setiap File:

1. `config.ts`: Berisi URL API dan pengaturan default
2. `auth.ts`: Fungsi untuk login, register, logout
3. `loyalty.ts`: Fungsi untuk sistem point/reward
4. `index.ts`: Mengumpulkan semua fungsi API
5. `AuthContext.tsx`: Menyimpan data user dan status login
6. `useAuth.ts`: Hook untuk menggunakan AuthContext

## Alur Sederhana:

1. User klik tombol "Sign In"
2. Halaman memanggil `login()` dari `useAuth()`
3. `login()` memanggil `loginUser()` dari service API
4. API mengirim data ke server
5. Hasil disimpan di AuthContext
6. User diarahkan ke dashboard jika berhasil

Apakah ini cukup jelas? Adakah bagian spesifik yang Anda ingin saya jelaskan lebih detail?
