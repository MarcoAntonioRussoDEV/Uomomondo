<template>
  <div>
    <Section>
      <Card
        card-title="Il tema di quest'anno"
        :img-src="thumbImagePath"
        class="bg-primary"
        button-text="galleria completa"
        button-action="gallery/2023-24"
        reverse
      >
        <p>
          Il tema di quest’anno è
          <strong>“Pace e responsabilità”</strong>. La guerra è un tema attuale, che ci coinvolge
          tutti. La pace è un valore da perseguire, da costruire quotidianamente.
        </p>
        <Carousel class="rounded-4xl" />
      </Card>
    </Section>
    <Section>
      <div class="flex w-full">
        <Stepper :steps="years" class="px-8 hidden xl:inline-grid" />
        <div class="flex w-full flex-col gap-4">
          <CardText
            v-for="year of years"
            :card-title="year.theme"
            class="bg-base-200 w-full"
            button-text="galleria completa"
            :button-action="`/gallery/${year.year}`"
          >
            <Carousel class="rounded-4xl" />
          </CardText>
        </div>
      </div>
    </Section>
  </div>
</template>

<script>
import Section from '@/components/Section.vue'
import Card from '@/components/Card.vue'
import CardText from '@/components/CardText.vue'
import Carousel from '@/components/Carousel.vue'
import Stepper from '@/components/Stepper.vue'

const years = [
  { year: '2013-14', theme: 'Costruire (anche) attraverso il conflitto' },
  { year: '2014-15', theme: 'Economia solidale e pace' },
  { year: '2015-16', theme: 'Religioni, terrorismi, guerra e pace' },
  { year: '2016-17', theme: 'Agenda 2030, ecologia e pace' },
  { year: '2017-18', theme: 'Costruire la comunità partendo dalla pace' },
  { year: '2018-19', theme: 'Migrazioni e culture: incontro o scontro?' },
  { year: '2019-20', theme: 'I care: pace è prendersi cura' },
  { year: '2020-21', theme: 'Speranze di pace' },
  { year: '2021-22', theme: "L'ambiente e la sua cura" },
  { year: '2022-23', theme: 'Il viaggio di Penelope' },
  { year: '2023-24', theme: 'Pace e responsabilità' },
]

export default {
  name: 'GalleryView',
  components: {
    Section,
    Card,
    CardText,
    Carousel,
    Stepper,
  },
  data() {
    return {
      years: years.reverse().slice(1, years.length),
      thumbImagePath: `${import.meta.env.BASE_URL}thumb.png`,
    }
  },
}
</script>

<style scoped></style>
