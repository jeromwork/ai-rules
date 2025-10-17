# Vue Browser Automation Rules

**Scope:** 
- `include`: ["**/*.vue", "**/src/**", "**/public/**", "**/vite.config.*", "**/package.json"]
- `exclude`: ["**/node_modules/**", "**/dist/**"]

## MANDATORY: Auto-Start Browser Automation for Vue Projects

### 1. Browser Initialization (MUST)
- **ALWAYS** check if MCP browser is connected before any Vue component testing
- **AUTOMATICALLY** start MCP browser server if not running
- **AUTOMATICALLY** navigate to project admin panel when starting Vue development work
- **VERIFY** Vue application loads correctly before proceeding with tasks

### 2. Port Management (AUTOMATIC)
- **BEFORE** any browser operation, run: `scripts\manage-ports.bat status`
- **IF** port 9009 is free, run: `scripts\manage-ports.bat start`
- **IF** port 9009 is occupied, kill process and restart: `taskkill /F /PID <PID>`
- **ENSURE** Vite dev server is running on port 3081

### 3. Default Navigation (AUTOMATIC)
- **ALWAYS** start with: `http://localhost:3081/nimda-panel/#/`
- **VERIFY** Vue application loads successfully before proceeding
- **IF** page fails to load, check Vite server status and restart if needed
- **TAKE** initial snapshot to verify Vue components are rendering

### 4. Vue-Specific Browser Operations
- **TEST** Vue component interactions (clicks, form submissions, navigation)
- **VERIFY** Vue reactivity and state management through browser
- **CHECK** Vue router navigation and route changes
- **VALIDATE** Vue component props and events through browser inspection

### 5. Browser State Management
- **MAINTAIN** browser session throughout the conversation
- **REFRESH** page if Vue application becomes unresponsive
- **RESTART** MCP server if connection is lost
- **PRESERVE** Vue component state when possible

## Vue Browser Operation Workflow

### Phase 1: Initialization
1. Check port status: `scripts\manage-ports.bat status`
2. Start MCP server if needed: `npx @browsermcp/mcp@latest`
3. Ensure Vite dev server is running: `npm run dev`
4. Navigate to admin panel: `http://localhost:3081/nimda-panel/#/`
5. Verify Vue application loads and take snapshot

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

## Vue Component Testing with Browser

### Component Interaction Testing
- **CLICK** buttons and links to test event handlers
- **FILL** forms to test v-model and form validation
- **NAVIGATE** between routes to test Vue router
- **TOGGLE** component visibility and state

### State Management Testing
- **VERIFY** Vuex/Pinia state changes through browser
- **TEST** component props and computed properties
- **VALIDATE** component events and parent-child communication

### Styling and Responsive Testing
- **CHECK** component styling and CSS classes
- **TEST** responsive behavior at different screen sizes
- **VERIFY** PrimeVue component styling and theming

## Integration with Vue Development Workflow

This browser automation system integrates with Vue development:

1. **Before any Vue component task**: Auto-start browser and navigate to admin panel
2. **During Vue development**: Use browser for component testing and verification
3. **After Vue changes**: Use browser to verify component functionality
4. **For Vue debugging**: Use browser tools to inspect component state and props

## Success Criteria for Vue Projects

- ✅ MCP browser server running on port 9009
- ✅ Vite dev server running on port 3081
- ✅ Vue admin panel accessible at `http://localhost:3081/nimda-panel/#/`
- ✅ Browser extension connected and responsive
- ✅ Vue components rendering correctly
- ✅ Vue router navigation working
- ✅ All Vue component interactions working without errors

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

