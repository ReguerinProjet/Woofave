<!-- components/Search.vue -->

<template>
  <div class="search-cont inline-flex gap-2 bg-white p-2 rounded-lg shadow-lg">
    <ais-instant-search index-name="articles" :search-client="searchClient">
      <ais-configure
        :attributesToSnippet="['bodyPlainText']"
        :hits-per-page.camel="5"
        snippetEllipsisText="…"
      >
        <ais-autocomplete>
          <template v-slot="{ currentRefinement, indices, refine }">
            <input
              type="search"
              :value="currentRefinement"
              placeholder="Search for an article"
              @input="refine($event.currentTarget.value)"
            />
            <ais-stats />
            <template v-if="currentRefinement">
              <ul v-for="index in indices" :key="index.indexId">
                <li>
                  <h3>{{ index.indexName }}</h3>
                  <ul>
                    <li v-for="hit in index.hits" :key="hit.objectID">
                      <h1>
                        <ais-highlight attribute="title" :hit="hit" />
                      </h1>
                      <h2>
                        <ais-highlight attribute="description" :hit="hit" />
                      </h2>
                      <p>
                        <ais-snippet attribute="bodyPlainText" :hit="hit" />
                      </p>
                    </li>
                  </ul>
                </li>
              </ul>
            </template>
            <ais-pagination />
          </template>
        </ais-autocomplete>
      </ais-configure>
    </ais-instant-search>
  </div>
</template>

<script>
export default {
  name: 'SearchBar'
}
</script>