<script lang="ts">
  import * as Accordion from '$lib/components/ui/accordion/index.js'

  const examTypes = [
    {
      title: 'Zugangskolloquium',
      content: ''
    },
    {
      title: 'Präparat',
      content: ''
    },
    {
      title: 'Mündlicher Beitrag',
      content:
        'Ein mündlicher Beitrag (z. B. Referat, Präsentation, Verhandlung, Moderation) dient der Feststellung, ob die Studierenden befähigt sind, innerhalb einer vorgegebenen Frist eine praxisorientierte Aufgabe nach wissenschaftlichen und fachpraktischen Methoden selbstständig zu bearbeiten und mittels verbaler Kommunikation fachlich angemessen darzustellen. Die Dauer des mündlichen Beitrags wird von der Prüferin beziehungsweise dem Prüfer zu Beginn des Semesters festgelegt.'
    },
    {
      title: 'Hausarbeit',
      content:
        'Eine Hausarbeit (z.B. Fallstudie, Recherche) dient der Feststellung, ob die Studierenden befähigt sind, innerhalb einer vorgegebenen Frist eine Fachaufgabe nach wissenschaftlichen und fachpraktischen Methoden selbstständig in schriftlicher Form zu bearbeiten. Das Thema und der Umfang (z. B. Seitenzahl des Textteils) der Hausarbeit werden von der Prüferin beziehungsweise dem Prüfer zu Beginn des Semesters festgelegt.'
    },
    {
      title: 'Projektarbeit',
      content: ''
    },
    {
      title: 'Lernportfolio',
      content:
        'Ein Lernportfolio dokumentiert den studentischen Kompetenzentwicklungsprozess anhand von Präsentationen, Essays, Ausschnitten aus Praktikumsberichten, Inhaltsverzeichnissen von Hausarbeiten, Vorlesungsmitschriften, To-Do-Listen, Forschungsberichten und anderen Leistungsdarstellungen und Lernproduktionen, zusammengefasst als sogenannte „Artefakte“. Nur in Verbindung mit der studentischen Reflexion (schriftlich, mündlich oder auch in einem Video) der Verwendung dieser Artefakte für das Erreichen des zuvor durch die Prüferin oder den Prüfer transparent gemachten Lernziels wird das Lernportfolio zum Prüfungsgegenstand. Während der Erstellung des Lernportfolios wird von der Prüferin oder dem Prüfer im Semesterverlauf Feedback auf Entwicklungsschritte und/oder Artefakte gegeben. Als Prüfungsleistung wird eine nach dem Feedback überarbeitete Form des Lernportfolios – meist in elektronischer Form – eingereicht.'
    },
    {
      title: 'Praktikumsbericht',
      content: ''
    },
    {
      title: 'Open-Book-Ausarbeitung',
      content: ''
    },
    {
      title: 'Testat/Zwischentestat',
      content: ''
    },
    {
      title: 'Performanzprüfung',
      content: ''
    },
    {
      title: 'Rollenspiel',
      content: ''
    },
    {
      title: 'E-Prüfung',
      content:
        'Eine elektronische Klausur (eKlausur) ist eine Prüfung, die am Computer mittels eines Prüfungsprogramms durchgeführt wird und deren Erstellung, Durchführung und Auswertung insgesamt durch Informations- und Kommunikationstechnologien unterstützt wird. Den Studierenden wird vor der Prüfung ausreichend Gelegenheit gegeben, sich mit dem elektronischen Prüfungssystem vertraut zu machen.'
    },
    {
      title: 'Klausurarbeit',
      content: ''
    },
    {
      title: 'Schriftliche Prüfung im Antwortwahlverfahren (Multiple Choice)',
      content:
        'Klausurarbeiten können ganz oder teilweise in der Form des Antwortwahlverfahrens durchgeführt werden. Hierbei haben die Studierenden unter Aufsicht schriftlich gestellte Fragen durch die Angabe der für zutreffend befundenen Antworten aus einem Katalog vorgegebener Antwortmöglichkeiten zu lösen.'
    },
    {
      title: 'Mündliche Prüfung',
      content:
        'Diese Prüfungen werden entweder vor einer Prüferin oder einem Prüfer in Begleitung eines sachkundigen Beisitzers oder vor mehreren Prüfenden (als Kollegialprüfung) durchgeführt. Sie können sowohl als Gruppen- als auch als Einzelprüfungen abgelegt werden.'
    }
  ]

  const sortedExamTypes = examTypes.toSorted((a, b) => a.title.localeCompare(b.title))
</script>

<div class="w-full max-w-none space-y-8">
  <div class="flex gap-8">
    <!-- Main Content -->
    <main class="min-w-0 flex-1 space-y-12">
      <!-- Page Header -->
      <div class="space-y-2">
        <h2 class="text-3xl font-bold tracking-tight">Prüfungsformen</h2>
        <p class="text-muted-foreground text-sm wrap-break-word">
          Auf dieser Seite werden alle zulässigen Prüfungsformen gelistet und erklärt.
        </p>
      </div>

      <Accordion.Root type="single" class="w-full sm:max-w-[70%]">
        {#each sortedExamTypes as exam}
          <Accordion.Item disabled={!exam.content}>
            <Accordion.Trigger
              class={!exam.content ? 'text-muted-foreground cursor-not-allowed' : ''}
            >
              {exam.title}
            </Accordion.Trigger>
            {#if exam.content}
              <Accordion.Content class="flex flex-col gap-4 text-balance">
                <p>{exam.content}</p>
              </Accordion.Content>
            {/if}
          </Accordion.Item>
        {/each}
      </Accordion.Root>
    </main>
  </div>
</div>
