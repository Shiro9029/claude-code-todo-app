# 📝 Todo App - React Router v7 + Cloudflare Workers

Simple todo application built with modern web technologies for Cloudflare Workers platform.

## 🚀 Technology Stack

- **Frontend**: React 19 with React Router v7 (formerly Remix)
- **Database**: SQLite with Cloudflare D1
- **Testing**: Vitest (unit tests) + Playwright (E2E tests)
- **Platform**: Cloudflare Workers with Vite plugin v1.0
- **Deployment**: Cloudflare Workers (not Pages)

## 🏗️ Project Architecture

- React Router v7 handles both client and server-side rendering
- D1 SQLite database for todo storage
- Cloudflare Workers runtime for backend APIs
- Vite for development and build process

## ⚡ Development Commands

- **Start dev server**: `npm run dev`
- **Build**: `npm run build`
- **Preview build**: `npm run preview`
- **Deploy**: `npx wrangler deploy`
- **Test unit**: `npm run test`
- **Test E2E**: `npm run test:e2e`
- **Lint**: `npm run lint`
- **Type check**: `npm run typecheck`

## 🔄 Development Workflow

### Local Development
- Use `npm run dev` with Cloudflare Vite plugin
- Database persists with `--persist-to` option in wrangler
- Live reload works for UI changes
- Worker code changes require manual refresh

### Database Setup
```bash
# Create D1 database
npx wrangler d1 create todo-db

# Run migrations
npx wrangler d1 migrations apply todo-db --local
npx wrangler d1 migrations apply todo-db --remote
```

## 🧪 Testing Strategy

### Unit Testing (Vitest)
- Component testing with Vitest Browser Mode
- Uses Playwright provider for real browser testing
- Configuration in `vitest.config.ts`
- Run with `npm run test`

### E2E Testing (Playwright)
- Full application flow testing
- Tests against deployed Workers environment
- Configuration in `playwright.config.ts`
- Run with `npm run test:e2e`

## 🚢 Deployment Process

1. **Build application**: `npm run build`
2. **Run tests**: `npm run test && npm run test:e2e`
3. **Deploy to Workers**: `npx wrangler deploy`
4. **Verify deployment**: Check Workers dashboard

## 📋 Code Standards

- Use TypeScript for type safety
- 2-space indentation
- Prefer functional components with hooks
- Use React Router v7 data loading patterns
- Follow Cloudflare Workers best practices

## 📁 File Structure

```
src/
├── routes/           # React Router v7 route modules
├── components/       # Reusable React components
├── lib/             # Utility functions and database
├── styles/          # CSS modules or Tailwind
└── worker.ts        # Cloudflare Worker entry point
```

## ⚠️ Important Notes

- Use Workers (not Pages) for new projects - all Cloudflare investment is in Workers
- D1 database sharing between dev instances may affect live reload
- Vite 6 Environment API provides Worker runtime alignment
- React Router v7 is production-ready on Cloudflare Workers as of 2025

## 🔧 Environment Variables

```bash
# .env.local
DATABASE_URL="your-d1-database-url"
```

## 🔍 Troubleshooting

- **Live reload issues**: Check `--persist-to` flag usage
- **Build failures**: Verify all dependencies are properly installed
- **Database errors**: Ensure D1 migrations are applied
- **Worker deployment**: Check wrangler.toml configuration