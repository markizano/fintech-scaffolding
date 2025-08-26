# Cal.com Angular Component

A parameterized Angular component for embedding Cal.com scheduling widgets.

## Features

- **Extracted Scripts**: All JavaScript moved from HTML template to TypeScript component
- **Parameterized**: Configurable inputs for different meeting types and settings
- **SSR Safe**: Proper browser detection to avoid issues with server-side rendering
- **Type Safe**: Full TypeScript support with proper interfaces
- **Multiple Instances**: Support for multiple Cal.com embeds on the same page

## Usage

### Basic Usage (Swedish massage - default)

```html
<app-cal-com></app-cal-com>
```

### Custom Meeting Type

```html
<app-cal-com
  meetingType="deepTissue"
  calLink="kizanos.massage/deep-tissue">
</app-cal-com>
```

### Full Customization

```html
<app-cal-com
  meetingType="consultation"
  calLink="kizanos.massage/consultation"
  width="800px"
  height="600px"
  [config]="{layout: 'week_view'}"
  [uiConfig]="{
    cssVarsPerTheme: {
      light: {'cal-brand': '#123100'},
      dark: {'cal-brand': '#9DE672'}
    },
    hideEventTypeDetails: false,
    layout: 'week_view'
  }">
</app-cal-com>
```

## Input Properties

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `meetingType` | `string` | `'swedish'` | Unique identifier for the meeting type |
| `calLink` | `string` | `'kizanos.massage/swedish'` | Cal.com link for the booking |
| `origin` | `string` | `'https://app.cal.com'` | Cal.com origin URL |
| `width` | `string` | `'100%'` | Container width |
| `height` | `string` | `'100%'` | Container height |
| `config` | `CalConfig` | `{layout: 'month_view'}` | Cal.com embed configuration |
| `uiConfig` | `CalUIConfig` | Default theme config | UI styling configuration |

## Interfaces

### CalConfig

```typescript
interface CalConfig {
  layout?: 'month_view' | 'week_view' | 'column_view';
  [key: string]: any;
}
```

### CalUIConfig

```typescript
interface CalUIConfig {
  cssVarsPerTheme?: {
    light?: { [key: string]: string };
    dark?: { [key: string]: string };
  };
  hideEventTypeDetails?: boolean;
  layout?: 'month_view' | 'week_view' | 'column_view';
  [key: string]: any;
}
```

## Migration from Old Version

### Before (hardcoded script in HTML)

```html
<!-- Cal inline embed code begins -->
<div style="width:100%;height:100%;overflow:scroll" id="my-cal-inline-swedish"></div>
<script type="text/javascript">
  // ... hardcoded Cal.com script for 'swedish' only
</script>
```

### After (parameterized component)

```html
<app-cal-com meetingType="swedish" calLink="kizanos.massage/swedish"></app-cal-com>
```

## Benefits

1. **Reusable**: Can be used for multiple meeting types
2. **Maintainable**: Script logic centralized in TypeScript
3. **Type Safe**: Full TypeScript support with interfaces
4. **SSR Compatible**: Proper browser detection
5. **Clean HTML**: No embedded scripts in templates
6. **Configurable**: All Cal.com options exposed as inputs
