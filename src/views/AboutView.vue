<template>
  <Section>
    <Card card-title="Chi siamo" img-src="/cross_arms.png" reverse class="bg-primary">
      <p>
        Il progetto nasce dall'impegno della prof.ssa <strong> Maria Fedele</strong>, che nel 2006
        aderisce, per conto dell'Istituto, a una rete di scuole denominata
        <strong>UOMO MONDO FOR UNITY</strong>.
      </p>
      <p>
        Tale rete, sotto la direzione della prof.ssa Maria Altamura, di Corato (BA), si componeva di
        diverse scuole della <strong>Puglia</strong> e intesseva contatti con reti omonime di scuole
        albanesi, macedoni e di altre nazioni balcaniche. Il tutto era nato dopo che le coste
        pugliesi erano diventate punto di approdo di centinaia di migliaia di migranti da quei
        paesi, negli anni '90. Si avevano anche rapporti di collaborazione con la Rete Progetto Pace
        di Treviso.
      </p>
      <p>
        Attualmente la Rete di scuole UOMO MONDO FOR UNITY della Puglia non esiste più, anche perchè
        a molte scuole sembra che siano venuti meno i presupposti iniziali.
      </p>
      <p>
        Il <strong>Liceo Marconi</strong> ha continuato le attività trasformandosi in un progetto di
        ampio respiro, di sensibilizzazione nell'Istituto e nel proprio territorio.
      </p>
      <p>Dal 2011 il curatore del progetto è il prof. <strong>Michele Quintana</strong>.</p>
    </Card>
  </Section>
  <Section>
    <Card
      card-title="Gli obiettivi"
      img-src="/point.png"
      class="bg-base-200"
      button-text="Unisciti a noi"
      reverse
      >Il Progetto “Uomo-mondo. La pace, l’impegno, la condivisione” è pensato come un ambito
      educativo in cui i ragazzi si sentano protagonisti, pur guidati dai docenti formatori.
      All’interno del Progetto molte scelte vengono condivise tra docenti ed alunni e sempre
      motivate. I ragazzi partecipano anche alle fasi decisionali riguardanti il tema dell’anno e
      alle modalità di attuazione dell’intervento formativo, nonché alla verifica finale. Un
      obiettivo del team di docenti formatori è anche quello di creare gruppo fra i ragazzi che,
      provenendo da classi diverse, inizialmente non si conoscono. Si favorisce in questo modo anche
      una “riconoscibilità” all’interno dell’Istituto. Inoltre il Progetto, che originariamente è
      nato da una rete di scuole, pur non avendo più una rete di stretto riferimento, cerca
      l’incontro con altre scuole, associazioni, istituzioni operanti nel territorio, offrendo così
      agli studenti strumenti per collegare fra loro le varie esperienze, per un arricchimento
      reciproco e una maggiore incidenza. Il Progetto, attraverso le attività che propone (incontri
      in sede, incontri sul territorio, conferenze-convegni-meeting, viaggi interculturali e di
      solidarietà), si propone una formazione globale della personalità dei ragazzi, che vengono
      abituati al confronto con persone di culture diverse e in situazioni pedagogicamente e
      didatticamente differenti dall'usuale metodo scolastico. Tutto questo anche attraverso la
      concretizzazione, nella propria vita, di quanto hanno appreso e sperimentato.
    </Card>
  </Section>
</template>

<script>
import Section from '@/components/Section.vue'
import Card from '@/components/Card.vue'

export default {
  name: 'AboutView',
  components: {
    Section,
    Card,
  },
}
</script>

<style scoped></style>
