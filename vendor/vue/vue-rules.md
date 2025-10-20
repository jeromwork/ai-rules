# Vue Project Rules

**Scope:** 
- `include`: ["**/*.vue", "**/src/**", "**/public/**", "**/vite.config.*", "**/package.json"]
- `exclude`: ["**/node_modules/**", "**/dist/**"]

## MANDATORY: Auto-Detection and Browser Automation for Vue Projects

### 1. Vue Project Detection (AUTOMATIC)
- **BEFORE** any Vue-related task, check if this is a Vue project
- **DETECT** Vue project by presence of: `package.json` with Vue dependencies, `vite.config.*`, `*.vue` files
- **ONLY** apply browser automation rules for confirmed Vue projects
- **SKIP** browser automation for non-Vue projects (React, Angular, vanilla JS, etc.)

### 2. Vue Project Detection Criteria
```json
// package.json must contain Vue dependencies
{
  "dependencies": {
    "vue": "^3.x.x" // or vue@2.x.x
  },
  "devDependencies": {
    "vite": "^4.x.x", // or webpack, rollup
    "@vitejs/plugin-vue": "^4.x.x" // Vue-specific build tools
  }
}
```

**File Structure Indicators:**
- `src/` directory with `.vue` files
- `vite.config.js` or `vite.config.ts`
- `public/` directory
- Vue-specific folders: `components/`, `views/`, `composables/`

### 3. Auto Browser Initialization (MANDATORY for Vue)
- **ALWAYS** check MCP browser connection status when starting Vue work
- **AUTOMATICALLY** start MCP browser server if not running (port 9009)
- **AUTOMATICALLY** start Vite dev server if not running (port 3081)
- **AUTOMATICALLY** navigate to Vue admin panel: `http://localhost:3081/nimda-panel/#/`
- **VERIFY** Vue application loads correctly before proceeding

### 4. Port Management (AUTOMATIC)
- **BEFORE** any browser operation, run: `scripts\manage-ports.bat status`
- **IF** port 9009 is free, run: `scripts\manage-ports.bat start`
- **IF** port 9009 is occupied, kill process and restart: `taskkill /F /PID <PID>`
- **ENSURE** Vite dev server is running on port 3081

### 5. Default Navigation (AUTOMATIC)
- **ALWAYS** start with: `http://localhost:3081/nimda-panel/#/`
- **VERIFY** Vue application loads successfully before proceeding
- **IF** page fails to load, check Vite server status and restart if needed
- **TAKE** initial snapshot to verify Vue components are rendering

### 6. Vue-Specific Browser Operations
- **TEST** Vue component interactions (clicks, form submissions, navigation)
- **VERIFY** Vue reactivity and state management through browser
- **CHECK** Vue router navigation and route changes
- **VALIDATE** Vue component props and events through browser inspection

### 7. Browser State Management
- **MAINTAIN** browser session throughout the conversation
- **REFRESH** page if Vue application becomes unresponsive
- **RESTART** MCP server if connection is lost
- **PRESERVE** Vue component state when possible

## Vue Development Guidelines

### Component Development
- Use single-file components with `<script setup>`
- Keep components small; extract composables into `useFoo.ts`
- Enforce type safety with TypeScript where possible
- Avoid leaking secrets into client bundles

### Vue-Specific Browser Testing
- **CLICK** buttons and links to test event handlers
- **FILL** forms to test v-model and form validation
- **NAVIGATE** between routes to test Vue router
- **TOGGLE** component visibility and state
- **VERIFY** Vuex/Pinia state changes through browser
- **TEST** component props and computed properties
- **VALIDATE** component events and parent-child communication

## Vue Browser Operation Workflow

### Phase 1: Project Detection & Initialization
1. Check `package.json` for Vue dependencies
2. Look for Vue-specific files (`*.vue`, `vite.config.*`)
3. Confirm this is a Vue project before proceeding
4. Check port status: `scripts\manage-ports.bat status`
5. Start MCP server if needed: `npx @browsermcp/mcp@latest`
6. Start Vite dev server: `npm run dev`
7. Navigate to admin panel: `http://localhost:3081/nimda-panel/#/`
8. Verify Vue application loads and take snapshot

### Phase 2: Vue Development Tasks
1. Use browser tools for Vue component testing
2. Test Vue router navigation and route changes
3. Verify Vue component interactions and state changes
4. Test form submissions and data binding
5. Take snapshots before and after major actions

### Phase 3: Vue Testing & Validation
1. Test Vue component lifecycle methods through browser
2. Verify Vuex/Pinia state management
3. Test Vue component communication (props, events, slots)
4. Validate Vue component styling and responsive behavior

### Phase 4: Cleanup
1. Keep browser session active for follow-up Vue tasks
2. Only close browser when explicitly requested
3. Maintain MCP server running for future Vue operations

## Vue-Specific Error Handling

### Vue Project Detection Errors
- **IF** Vue dependencies not found: Skip browser automation
- **IF** Vue files not present: Skip browser automation
- **IF** project type unclear: Ask user for confirmation

### Vue Application Issues
- **IF** Vue app fails to load: check Vite server and restart
- **IF** Vue components not rendering: check console for Vue errors
- **IF** Vue router navigation fails: verify route configuration
- **IF** Vue state not updating: check Vuex/Pinia store configuration

### MCP Server Issues
- **IF** "Not connected" error: restart MCP server
- **IF** "Port occupied" error: kill process and restart
- **IF** "WebSocket timeout" error: check server status and restart

### Browser Extension Issues
- **IF** "No connection to browser extension" error: instruct user to connect extension
- **IF** page fails to load: check Vite server and restart if needed

## Vue Development Commands

### Port Management
```bash
# Check status
scripts\manage-ports.bat status

# Start services
scripts\manage-ports.bat start

# Stop services
scripts\manage-ports.bat stop
```

### Vue Development
```bash
# Start Vite dev server
npm run dev

# Or use setup command (includes port management)
npm run setup

# Build for production
npm run build

# Preview production build
npm run preview
```

### MCP Server
```bash
# Start MCP server
npx @browsermcp/mcp@latest

# Check if running
netstat -ano | findstr :9009
```

## Vue-Specific Browser Tools Usage

### Navigation
- Use `mcp_browsermcp_browser_navigate` for route changes
- Use `mcp_browsermcp_browser_click` for component interactions
- Use `mcp_browsermcp_browser_type` for form inputs

### Inspection
- Use `mcp_browsermcp_browser_snapshot` to verify component rendering
- Use `mcp_browsermcp_browser_get_console_logs` to check Vue errors
- Use `mcp_browsermcp_browser_screenshot` for visual verification

### Interaction
- Use `mcp_browsermcp_browser_hover` for hover effects
- Use `mcp_browsermcp_browser_select_option` for dropdown selections
- Use `mcp_browsermcp_browser_press_key` for keyboard interactions

## Integration with Vue Development Workflow

This browser automation system integrates with Vue development:

1. **Before any Vue component task**: Auto-detect Vue project and start browser automation
2. **During Vue development**: Use browser for component testing and verification
3. **After Vue changes**: Use browser to verify component functionality
4. **For Vue debugging**: Use browser tools to inspect component state and props

## Success Criteria for Vue Projects

### Vue Project Detection: ✅
- `package.json` contains Vue dependencies
- Vue-specific files present (`*.vue`, `vite.config.*`)
- Vue project structure confirmed

### Browser Automation Active: ✅
- MCP browser server running on port 9009
- Vite dev server running on port 3081
- Vue admin panel accessible
- Browser extension connected

### Ready for Vue Development: ✅
- Vue components can be tested in browser
- Vue router navigation working
- Vue state management accessible
- All Vue component interactions functional

## PR Notes
- Frontend changes must include screenshots or Storybook references where applicable
- Vue component changes must be tested in browser before submission
- All Vue router changes must be verified through browser navigation
