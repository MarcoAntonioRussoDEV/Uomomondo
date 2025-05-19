<template>
  <Section class="grid place-content-center">
    <Card
      card-title="404"
      img-src="/questioning.png"
      class="bg-primary"
      button-text="Torna alla Home"
      button-action="/"
      reverse
    >
      <p class="text-2xl">Sembra che la pagina che cerchi non sia disponibile</p>
    </Card>
  </Section>
</template>

<script>
import Card from '@/components/Card.vue'
import Section from '@/components/Section.vue'
export default {
  name: 'NotFoundView',
  components: {
    Card,
    Section,
  },
}
</script>

<style scoped></style>
