# Medical Store POS - Frontend

Production-ready Angular frontend for Medical Store POS system.

## Prerequisites

- Node.js 18+ 
- npm 9+

## Local Development

1. Install dependencies:
```bash
npm install
```

2. Update API URL in `src/environments/environment.ts`:
```typescript
apiUrl: 'http://localhost:8080/api'
```

3. Run development server:
```bash
npm start
```

4. Build for production:
```bash
npm run build
```

## Deployment

### Vercel (Recommended)

1. Install Vercel CLI:
```bash
npm i -g vercel
```

2. Deploy:
```bash
vercel
```

Or connect your GitHub repository directly to Vercel dashboard.

3. The production API URL is already configured in `src/environments/environment.prod.ts`:
   - Current: `https://medicalpos-backend.onrender.com/api`
   - To change: Update the `apiUrl` in `environment.prod.ts` before building

### Netlify

1. Build command: `npm run build`
2. Publish directory: `dist/medical-store-pos/browser`
3. The production API URL is already configured in `src/environments/environment.prod.ts`:
   - Current: `https://medicalpos-backend.onrender.com/api`

### Other Static Hosting

1. Build the project:
```bash
npm run build
```

2. Deploy the `dist/medical-store-pos/browser` folder to your hosting provider

## Environment Variables

The production API URL is configured in `src/environments/environment.prod.ts`:
- Current production API: `https://medicalpos-backend.onrender.com/api`
- Development API: `http://localhost:8080/api` (configured in `environment.ts`)

## Build Configuration

The project is configured to build with:
- Output directory: `dist/medical-store-pos/browser`
- Base href: `/`
- Production optimizations enabled

## Troubleshooting

### API URL Still Shows localhost:8080 After Deployment

If the deployed application is still trying to connect to `localhost:8080`, check:

1. **Verify Build Configuration**: Ensure `angular.json` has `fileReplacements` in the production configuration
2. **Clear Build Cache**: Delete `node_modules` and `.angular` folders, then rebuild
3. **Browser Cache**: Clear browser cache or use incognito mode to test
4. **Vercel Build Logs**: Check Vercel build logs to ensure production configuration is used
5. **Verify Environment File**: Check that `environment.prod.ts` has the correct API URL

### Build Verification

To verify the build uses the correct environment:

```bash
# Build the project
npm run build

# Check the built main.js file (it should contain the production API URL)
grep -r "medicalpos-backend.onrender.com" dist/medical-store-pos/browser/
```

## Notes

- The production API URL is already configured to `https://medicalpos-backend.onrender.com/api`
- To change the API URL, update `src/environments/environment.prod.ts` before building
- The frontend uses Angular routing, so ensure your hosting provider supports SPA routing (all routes redirect to index.html)
- The build script automatically uses production configuration with environment file replacement

