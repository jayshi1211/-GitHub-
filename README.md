name: Project Management

on:
  issues:
    types: [assigned]

jobs:
  manage-issue:
    runs-on: ubuntu-latest
    steps:
      - name: Move issue to assigned column
        uses: actions/github-script@v6
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          script: |
            github.issues.moveIssueToColumn({
              issue_number: github.context.issue.number,
              column_id: '1234567890' // 指定欄位ID
            })
