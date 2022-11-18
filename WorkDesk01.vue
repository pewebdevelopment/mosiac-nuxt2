        
        
        <template>
  <!-- Dashboard -->
  <SidebarLinkGroup
    v-slot="parentLink"
    :activeCondition="
      $route.fullPath === '/' || $route.fullPath.includes('dashboard')
    "
  >
    <a
      class="
        block
        text-slate-200
        hover:text-white
        truncate
        transition
        duration-150
      "
      :class="
        ($route.fullPath === '/' || $route.fullPath.includes('dashboard')) &&
        'hover:text-slate-200'
      "
      href="#0"
      @click.prevent="
        sidebarExpanded ? parentLink.handleClick() : (sidebarExpanded = true)
      "
    >
      <div class="flex items-center justify-between">
        <div class="flex items-center">
          <svg class="shrink-0 h-6 w-6" viewBox="0 0 24 24">
            <path class="fill-current text-slate-400" :class$route.fullPath ===
            '/' || $route.fullPath.includes('dashboard')) && '!text-indigo-500'
            " d="M12 0C5.383 0 0 5.383 0 12s5.383 12 12 12 12-5.383 12-12S18.617
            0 12 0z" />
            <path
              class="fill-current text-slate-600"
              :class="
                ($route.fullPath === '/' ||
                  $route.fullPath.includes('dashboard')) &&
                'text-indigo-600'
              "
              d="M12 3c-4.963 0-9 4.037-9 9s4.037 9 9 9 9-4.037 9-9-4.037-9-9-9z"
            />
            <path
              class="fill-current text-slate-400"
              :class="
                ($route.fullPath === '/' ||
                  $route.fullPath.includes('dashboard')) &&
                'text-indigo-200'
              "
              d="M12 15c-1.654 0-3-1.346-3-3 0-.462.113-.894.3-1.285L6 6l4.714 3.301A2.973 2.973 0 0112 9c1.654 0 3 1.346 3 3s-1.346 3-3 3z"
            />
          </svg>
          <span
            class="
              text-sm
              font-medium
              ml-3
              lg:opacity-0 lg:sidebar-expanded:opacity-100
              2xl:opacity-100
              duration-200
            "
            >Dashboard</span
          >
        </div>
        <!-- Icon -->
        <div class="flex shrink-0 ml-2">
          <svg
            class="w-3 h-3 shrink-0 ml-1 fill-current text-slate-400"
            :class="parentLink.expanded && 'rotate-180'"
            viewBox="0 0 12 12"
          >
            <path d="M5.9 11.4L.5 6l1.4-1.4 4 4 4-4L11.3 6z" />
          </svg>
        </div>
      </div>
    </a>
    <div class="lg:hidden lg:sidebar-expanded:block 2xl:block">
      <ul class="pl-9 mt-1" :class="!parentLink.expanded && 'hidden'">
        <nuxt-link to="/" custom v-slot="{ href, navigate, isExactActive }">
          <li class="mb-1 last:mb-0">
            <a
              class="
                block
                text-slate-400
                hover:text-slate-200
                transition
                duration-150
                truncate
              "
              :class="isExactActive && '!text-indigo-500'"
              :href="href"
              @click="navigate"
            >
              <span
                class="
                  text-sm
                  font-medium
                  lg:opacity-0 lg:sidebar-expanded:opacity-100
                  2xl:opacity-100
                  duration-200
                "
                >Main</span
              >
            </a>
          </li>
        </nuxt-link>
        <nuxt-link
          to="/dashboard/analytics"
          custom
          v-slot="{ href, navigate, isExactActive }"
        >
          <li class="mb-1 last:mb-0">
            <a
              class="
                block
                text-slate-400
                hover:text-slate-200
                transition
                duration-150
                truncate
              "
              :class="isExactActive && '!text-indigo-500'"
              :href="href"
              @click="navigate"
            >
              <span
                class="
                  text-sm
                  font-medium
                  lg:opacity-0 lg:sidebar-expanded:opacity-100
                  2xl:opacity-100
                  duration-200
                "
                >Analytics</span
              >
            </a>
          </li>
        </nuxt-link>
        <nuxt-link
          to="/dashboard/fintech"
          custom
          v-slot="{ href, navigate, isExactActive }"
        >
          <li class="mb-1 last:mb-0">
            <a
              class="
                block
                text-slate-400
                hover:text-slate-200
                transition
                duration-150
                truncate
              "
              :class="isExactActive && '!text-indigo-500'"
              :href="href"
              @click="navigate"
            >
              <span
                class="
                  text-sm
                  font-medium
                  lg:opacity-0 lg:sidebar-expanded:opacity-100
                  2xl:opacity-100
                  duration-200
                "
                >Fintech</span
              >
            </a>
          </li>
        </nuxt-link>
      </ul>
    </div>
  </SidebarLinkGroup>
</template>
        
        
      