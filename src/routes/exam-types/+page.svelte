<script lang="ts">
  import * as Accordion from '$lib/components/ui/accordion/index.js'

  const examTypes = [
    {
      title: 'Zugangskolloquium',
      content:
        'Ein Zugangskolloquium dient der Feststellung, ob die Studierenden die versuchsspezifischen Voraussetzungen erfüllen, eine definierte laborpraktische Aufgabe nach wissenschaftlichen und fachpraktischen Methoden selbstständig und sicher bearbeiten zu können.'
    },
    {
      title: 'Präparat',
      content:
        'Ein Präparat ist das materielle Produkt einer Arbeitsleistung, das hinsichtlich seiner Qualität und Quantität zuvor festgelegten Kriterien genügt. Es dient der Feststellung, ob der Prüfling befähigt ist, innerhalb vorgegebener Fristen eine Aufgabe mit dem Ziel der Herstellung eines Produktes nach wissenschaftlichen und fachpraktischen Methoden selbstständig zu bearbeiten.'
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
      content:
        'Die Projektarbeit ist eine Prüfungsleistung, die in der selbstständigen Bearbeitung einer spezifischen Fragestellung unter Anleitung mit wissenschaftlicher Methodik und einer Dokumentation der Ergebnisse besteht.'
    },
    {
      title: 'Lernportfolio',
      content:
        'Ein Lernportfolio dokumentiert den studentischen Kompetenzentwicklungsprozess anhand von Präsentationen, Essays, Ausschnitten aus Praktikumsberichten, Inhaltsverzeichnissen von Hausarbeiten, Vorlesungsmitschriften, To-Do-Listen, Forschungsberichten und anderen Leistungsdarstellungen und Lernproduktionen, zusammengefasst als sogenannte „Artefakte“. Nur in Verbindung mit der studentischen Reflexion (schriftlich, mündlich oder auch in einem Video) der Verwendung dieser Artefakte für das Erreichen des zuvor durch die Prüferin oder den Prüfer transparent gemachten Lernziels wird das Lernportfolio zum Prüfungsgegenstand. Während der Erstellung des Lernportfolios wird von der Prüferin oder dem Prüfer im Semesterverlauf Feedback auf Entwicklungsschritte und/oder Artefakte gegeben. Als Prüfungsleistung wird eine nach dem Feedback überarbeitete Form des Lernportfolios – meist in elektronischer Form – eingereicht.'
    },
    {
      title: 'Praktikumsbericht',
      content:
        'Ein Praktikumsbericht (z. B. Versuchsprotokoll) dient der Feststellung, ob die Studierenden befähigt sind, innerhalb einer vorgegebenen Frist eine laborpraktische Aufgabe selbstständig sowohl praktisch zu bearbeiten als auch Bearbeitungsprozess und Ergebnis schriftlich zu dokumentieren, zu bewerten und zu reflektieren. Praktikumsberichte können auch in Form einer Gruppenarbeit zur Prüfung zugelassen werden. Die Bewertung des Praktikumsberichts ist den Studierenden spätestens sechs Wochen nach Abgabe des Berichts bekannt zu geben.'
    },
    {
      title: 'Open-Book-Ausarbeitung',
      content:
        'Die Open-Book-Ausarbeitung oder -Arbeit (OBA) ist eine Kurzhausarbeit und damit eine unbeaufsichtigte schriftliche oder elektronische Prüfung. Sie zeichnet sich dadurch aus, dass gemäß Hilfsmittelerklärung der Prüferin bzw. des Prüfers in der Regel alle Hilfsmittel zugelassen sind. Auf die Sicherung guter wissenschaftlicher Praxis durch ordnungsgemäßes Zitieren etc. und das Erfordernis der Eigenständigkeit der Erbringung jedweder Prüfungsleistung wird besonders hingewiesen.'
    },
    {
      title: 'Testat/Zwischentestat',
      content:
        'Mit einem Testat/Zwischentestat wird bescheinigt, dass die oder der Studierende eine Stu-dienarbeit (z.B. Entwurf) im geforderten Umfang erstellt hat. Der zu erbringende Leistungs-umfang sowie die geforderten Inhalte und Anforderungen ergeben sich aus der jeweiligen Modulbeschreibung im Modulhandbuch sowie aus der Aufgabenstellung.'
    },
    {
      title: 'Performanzprüfung',
      content:
        'Im Rahmen einer Performanzprüfung werden realitätsnahe, typische Handlungssituationen simuliert. Die Studierenden werden hierzu mit einer oder mehreren Aufgabenstellungen konfrontiert, wie sie in ihrem späteren Berufsfeld tatsächlich vorkommen (können). Die Studierenden müssen diese Aufgabenstellung – nach Maßgabe der konkreten Ausgestaltung in dem jeweiligen Modul – allein oder in der Rolle eines Mitglieds einer mit den jeweiligen Aufgaben betrauten Gruppe in eigener Verantwortung lösen. Wie sorgfältig die Aufgabenstellung analysiert und welcher Lösungsweg eingeschlagen wird, welche Methoden und Instrumente ausgewählt und eingesetzt werden und wie die Studierenden die eigenen Aktivitäten sowie die Zusammenarbeit mit den anderen Gruppenmitgliedern ausgestalten, organisieren, koordinieren und dokumentieren (Projektmanagement), bestimmen die Studierenden analog zur beruflichen Praxis weitgehend selbst; dies wird bewertet (Performanz).'
    },
    {
      title: 'Rollenspiel',
      content:
        'Ein Rollenspiel (auch Planspiel) dient der Feststellung, ob die Studierenden befähigt sind, innerhalb einer vorgegebenen Zeitspanne in einer praxisnahen oder praxisanalogen Situation bzw. Simulation Aufgaben mit wissenschaftlichen Methoden und unter Einsatz von Kommunikations- und Kooperationstechniken in der Regel im Diskurs mit weiteren handelnden, realen oder virtuellen Personen zu lösen. Die Bewertung ist den Studierenden nach Abschluss des Rollenspiels bekannt zu geben.'
    },
    {
      title: 'E-Prüfung',
      content:
        'Eine elektronische Klausur (eKlausur) ist eine Prüfung, die am Computer mittels eines Prüfungsprogramms durchgeführt wird und deren Erstellung, Durchführung und Auswertung insgesamt durch Informations- und Kommunikationstechnologien unterstützt wird. Den Studierenden wird vor der Prüfung ausreichend Gelegenheit gegeben, sich mit dem elektronischen Prüfungssystem vertraut zu machen.'
    },
    {
      title: 'Klausurarbeit',
      content:
        'Eine Klausurarbeit ist eine schriftliche Prüfung, in der die oder der Studierende unter Aufsicht und innerhalb einer begrenzten Zeit mit zugelassenen Hilfsmitteln nachweist, dass sie oder er Themen oder Fragestellungen eines Moduls mit den geläufigen wissenschaftlichen Methoden des jeweiligen Fachgebiets erkennen und sachgerecht lösen kann. Die Klausur findet in der Regel als Präsenzprüfung statt, kann jedoch auch elektronisch durchgeführt werden (eKlausur), einschließlich einer elektronischen Fernklausur. Elektronische Prüfungen werden wie schriftliche Prüfungen behandelt. Dabei wird sichergestellt, dass die Prüfungsbedingungen ordnungsgemäß überwacht, die Identität der Studierenden festgestellt und Täuschungen möglichst verhindert werden, unter Wahrung von Persönlichkeitsschutz und Privatsphäre. Die Prüfungsaufgabe wird in der Regel von einer Prüferin oder einem Prüfer gestellt und bewertet. In fachlich begründeten Fällen können mehrere Prüfende beteiligt sein; die Gewichtung der jeweiligen Anteile wird vorab festgelegt.'
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

      <Accordion.Root type="single" class="w-full sm:max-w-[65%]">
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
