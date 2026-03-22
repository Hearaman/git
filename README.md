# git

The purpose of our app is to empower engineering teams by enabling rapid application development without duplicate efforts, streamlining workflows through a centralized developer portal. It supports app modernisation with cloud native practices, integrating tools like Kubernetes and CI/CD pipelines for seamless scalability and resilience. This ensures consistency and compliance across projects by fostering organisation-specific golden paths. It reduces onboarding time by 50%, boosts productivity, and cuts costs. Ultimately, it transforms fragmented toolsets into a unified ecosystem, accelerating innovation and aligning tech initiatives with business goals for sustained growth.


```
// packages/app/src/modules/customLayoutModule.tsx
import React from 'react';
import {
  createExtension,
  createExtensionInput,
  coreExtensionData,
  createFrontendModule,
} from '@backstage/frontend-plugin-api';
import { SidebarPage } from '@backstage/core-components';
import { CustomMenubar } from '../components/CustomMenubar/CustomMenubar';

/**
 * Overrides the built-in `app/layout` extension.
 * 
 * The extension ID is derived from:
 *   pluginId (app) + name (layout) → "app/layout"
 * This matches the built-in extension ID, so it takes precedence.
 */
const customAppLayout = createExtension({
  // ⚠️ Must match the original name 'layout' within namespace 'app'
  name: 'layout',
  // ⚠️ Must match the original attachTo - attaches to app/root's 'children' input
  attachTo: { id: 'app/root', input: 'children' },
  inputs: {
    nav: createExtensionInput([coreExtensionData.reactElement], {
      singleton: true,
    }),
    content: createExtensionInput([coreExtensionData.reactElement], {
      singleton: true,
    }),
  },
  output: [coreExtensionData.reactElement],
  factory: ({ inputs }) => {
    const navElement = inputs.nav.get(coreExtensionData.reactElement);
    const contentElement = inputs.content.get(coreExtensionData.reactElement);

    return [
      coreExtensionData.reactElement(
        <SidebarPage>
          {/* Left sidebar (unchanged) */}
          {navElement}

          {/* Right content area — wrap with a flex column to stack menubar above content */}
          <div
            style={{
              display: 'flex',
              flexDirection: 'column',
              flex: 1,
              minWidth: 0,
              overflow: 'hidden',
            }}
          >
            {/* ✅ Your custom menubar injected here, above all page content */}
            <CustomMenubar />

            {/* Original page content (routes) rendered below */}
            {contentElement}
          </div>
        </SidebarPage>,
      ),
    ];
  },
});

/**
 * Frontend module targeting the built-in 'app' plugin.
 * The extension above overrides `app/layout` since it shares the same ID.
 */
export const appModuleCustomLayout = createFrontendModule({
  pluginId: 'app',
  extensions: [customAppLayout],
});


```
