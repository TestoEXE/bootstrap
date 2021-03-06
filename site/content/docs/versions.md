---
title: Versions
description: An appendix of hosted documentation for nearly every release of Bootstrap, from v1 through v4.
---

{{< versions.inline >}}
<div class="row">
{{ range $i, $release := (index $.Site.Data "docs-versions") }}
  <div class="col-md">
    <h2>{{ $release.group }}</h2>
    <p>{{ $release.description }}</p>
    {{ $versions := sort $release.versions "v" "desc" }}
    {{ range $j, $version := $versions }}
      {{ $len := len $versions }}
      {{ if (eq $j 0) }}<div class="list-group">{{ end }}
        {{ if (eq $version.v $.Site.Params.docs_version) }}
          <a class="list-group-item list-group-item-action py-2 text-primary d-flex justify-content-between align-items-center" href="{{ $release.baseurl }}/{{ $version.v }}/">
            {{ $version.v }}
            <span class="badge badge-primary">Latest</span>
          </a>
        {{ else }}
          <a class="list-group-item list-group-item-action py-2 text-primary" href="{{ $release.baseurl }}/{{ $version.v }}/">
            {{ $version.v }}
          </a>
        {{ end }}
      {{ if (eq (add $j 1) $len) }}</div>{{ end }}
    {{ end }}
  </div>
{{ end }}
</div>
{{< /versions.inline >}}
