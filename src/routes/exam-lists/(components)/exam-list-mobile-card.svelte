<script lang="ts">
  import { fmtDegree, fmtSemester, fmtStudyProgramName, getDateFormatter } from '$lib/formats'
  import Badge from '$lib/components/ui/badge/badge.svelte'
  import * as Card from '$lib/components/ui/card'
  import type { ExamList } from '$lib/types/exam-list'
  import { Calendar, GraduationCap } from '@lucide/svelte'
  import ExamListDownloadButton from './exam-list-download-button.svelte'

  let { examList }: { examList: ExamList } = $props()

  const df = getDateFormatter()
</script>

<Card.Root class="overflow-hidden transition-shadow hover:shadow-md">
  <Card.Header class="pb-2">
    <div class="flex items-start justify-between gap-3">
      <Card.Title class="flex-1 text-base leading-tight">
        {fmtStudyProgramName(examList.studyProgram)}
      </Card.Title>
      <div class="flex shrink-0 items-start gap-1.5">
        <Badge variant="secondary" class="text-xs">{fmtDegree(examList.studyProgram)}</Badge>
        <Badge variant="outline" class="text-xs">PO {examList.studyProgram.po.version}</Badge>
      </div>
    </div>
  </Card.Header>
  <Card.Content class="space-y-2.5 pb-4">
    <div class="flex items-center gap-2 text-sm">
      <GraduationCap class="text-muted-foreground size-4 shrink-0" />
      <span class="text-muted-foreground">Semester:</span>
      <span class="font-medium">{fmtSemester(examList.semester)}</span>
    </div>
    <div class="flex items-center gap-2 text-sm">
      <Calendar class="text-muted-foreground size-4 shrink-0" />
      <span class="text-muted-foreground">Veröffentlicht:</span>
      <span class="font-medium">{df.format(new Date(examList.date))}</span>
    </div>
  </Card.Content>
  <Card.Footer class="pt-0">
    <ExamListDownloadButton {examList} class="w-full" />
  </Card.Footer>
</Card.Root>
