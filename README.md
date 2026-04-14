# git

The purpose of our app is to empower engineering teams by enabling rapid application development without duplicate efforts, streamlining workflows through a centralized developer portal. It supports app modernisation with cloud native practices, integrating tools like Kubernetes and CI/CD pipelines for seamless scalability and resilience. This ensures consistency and compliance across projects by fostering organisation-specific golden paths. It reduces onboarding time by 50%, boosts productivity, and cuts costs. Ultimately, it transforms fragmented toolsets into a unified ecosystem, accelerating innovation and aligning tech initiatives with business goals for sustained growth.


```import {
  Sidebar,
  SidebarDivider,
  SidebarGroup,
  SidebarItem,
  SidebarScrollWrapper,
  SidebarSpace,
  SidebarSubmenu,
  SidebarSubmenuItem,
} from '@backstage/core-components';
import { NavContentBlueprint } from '@backstage/plugin-app-react';
import { SidebarSearchModal } from '@backstage/plugin-search';
import { useApp } from '@backstage/core-plugin-api';
import { UserSettingsSignInAvatar } from '@backstage/plugin-user-settings';
import { NotificationsSidebarItem } from '@backstage/plugin-notifications';
import { SidebarLogo } from './SidebarLogo';
import Divider from '@mui/material/Divider';

import {
  SearchIcon,
  MenuIcon,
  CatalogIcon,
  ComponentsIcon,
  ApisIcon,
  DocsIcon,
  ScaffolderIcon,
  TeamsIcon,
  SystemsIcon,
  DomainsIcon,
  CloudIcon,
  DatabaseIcon,
  GitIcon,
  MonitoringIcon,
  ObserveIcon,
  AnalyticsIcon,
  SecurityIcon,
  SecretsIcon,
  InfraIcon,
  TemplatesIcon,
  WorkflowIcon,
  TerminalIcon,
  PluginsIcon,
  SettingsIcon,
  HomeIcon,
  MousePointerClickIcon,
} from './icons';

export const SidebarContent = NavContentBlueprint.make({
  params: {
    component: ({ navItems }) => {
      const app = useApp();
      const nav = navItems.withComponent(item => (
        <SidebarItem icon={() => item.icon} to={item.href} text={item.title} />
      ));

      // Take items we'll place manually so they don't appear in nav.rest()
      nav.take('page:search');
      nav.take('page:catalog');
      nav.take('page:scaffolder');
      nav.take('page:app-visualizer');
      nav.take('page:user-settings');

      return (
        <Sidebar>
          <SidebarLogo />

          <SidebarDivider />

          {/* ── Main Navigation ──────────────────── */}
          <SidebarGroup label="Menu" icon={<MenuIcon />}>

            <SidebarItem icon={HomeIcon} to="/" text="Home" />

            {/* ── Catalog with sub-menu ────────────── */}
            <SidebarItem icon={CatalogIcon} to="catalog" text="Catalog">
              <SidebarSubmenu title="Catalog">
                <SidebarSubmenuItem
                  title="Components"
                  to="catalog?filters[kind]=component"
                  icon={app.getSystemIcon('kind:component')!}
                />
                <SidebarSubmenuItem
                  title="APIs"
                  to="catalog?filters[kind]=api"
                  icon={app.getSystemIcon('kind:api')!}
                />
                <SidebarSubmenuItem
                  title="Systems"
                  to="catalog?filters[kind]=system"
                  icon={app.getSystemIcon('kind:system')!}
                />
                <SidebarSubmenuItem
                  title="Domains"
                  to="catalog?filters[kind]=domain"
                  icon={app.getSystemIcon('kind:domain')!}
                />
                <SidebarDivider />
                <SidebarSubmenuItem
                  title="Resources"
                  to="catalog?filters[kind]=resource"
                  icon={app.getSystemIcon('kind:resource')!}
                />
                <SidebarSubmenuItem
                  title="Groups"
                  to="catalog?filters[kind]=group"
                  icon={app.getSystemIcon('kind:group')!}
                />
                <SidebarSubmenuItem
                  title="Users"
                  to="catalog?filters[kind]=user"
                  icon={app.getSystemIcon('kind:user')!}
                />
              </SidebarSubmenu>
            </SidebarItem>

            {/* ── Build & Deploy ────────────────────── */}
            <SidebarItem icon={MousePointerClickIcon} to="create" text="Self Service" />
            <SidebarItem icon={TemplatesIcon} to="catalog-import" text="Register" />
            <SidebarItem icon={GitIcon} to="ci-cd" text="CI/CD" />

            <SidebarDivider />

            {/* ── Develop ──────────────────────────── */}
            <SidebarItem icon={ApisIcon} to="api-docs" text="APIs" />
            <SidebarItem icon={DocsIcon} to="docs" text="TechDocs" />
            <SidebarItem icon={TerminalIcon} to="devtools" text="DevTools" />

            <SidebarDivider />

            {/* ── Infrastructure ────────────────────── */}
            <SidebarItem icon={CloudIcon} to="kubernetes" text="Kubernetes" />
            <SidebarItem icon={InfraIcon} to="infrastructure" text="Infra" />
            <SidebarItem icon={DatabaseIcon} to="resources" text="Resources" />

            <SidebarDivider />

            {/* ── Observe ──────────────────────────── */}
            <SidebarItem icon={MonitoringIcon} to="monitoring" text="Monitoring" />
            <SidebarItem icon={ObserveIcon} to="observability" text="Observe" />
            <SidebarItem icon={AnalyticsIcon} to="analytics" text="Analytics" />

            <SidebarDivider />

            {/* ── Govern ───────────────────────────── */}
            <SidebarItem icon={SecurityIcon} to="security" text="Security" />
            <SidebarItem icon={SecretsIcon} to="secrets" text="Secrets" />
            <SidebarItem icon={TeamsIcon} to="teams" text="Teams" />

            <SidebarDivider />

            {/* ── Extend ───────────────────────────── */}
            <SidebarItem icon={PluginsIcon} to="plugins" text="Plugins" />
            <SidebarItem icon={WorkflowIcon} to="workflows" text="Workflows" />

            <SidebarDivider />

            {/* ── Auto-discovered pages ─────────────── */}
            <SidebarScrollWrapper>
              {nav.rest({ sortBy: 'title' })}
            </SidebarScrollWrapper>

          </SidebarGroup>

          <SidebarSpace />

          {/* ── Bottom section ──────────────────── */}
          <SidebarDivider />
          <NotificationsSidebarItem />
          <SidebarDivider />
          <SidebarGroup
            label="Settings"
            icon={<UserSettingsSignInAvatar />}
            to="/settings"
          >
            <SidebarItem icon={ObserveIcon} to="app-visualizer" text="Visualizer" />
            <SidebarItem icon={SettingsIcon} to="settings" text="Settings" />
          </SidebarGroup>
        </Sidebar>
      );
    },
  },
});



```
