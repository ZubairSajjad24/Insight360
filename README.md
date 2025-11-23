{
  "name": "Insight360 Multi-Agent HR Intelligence Flow",
  "description": "Workflow representation of the three-agent orchestration running inside IBM watsonx Orchestrate.",
  "version": "1.0",
  "data_sources": [
    "Attendance Logs",
    "Wellbeing Records",
    "Training Data",
    "Performance Notes"
  ],
  "agents": [
    {
      "id": "audit_agent",
      "name": "Audit Agent",
      "receives": [
        "Attendance Logs",
        "Wellbeing Records",
        "Training Data",
        "Performance Notes"
      ],
      "produces": ["audit_summary"]
    },
    {
      "id": "opportunity_agent",
      "name": "Opportunity Discovery Agent",
      "receives": ["audit_summary"],
      "produces": ["opportunity_recommendations"]
    },
    {
      "id": "reporting_agent",
      "name": "Reporting Agent",
      "receives": ["opportunity_recommendations"],
      "produces": [
        "actionable_insights",
        "prioritized_recommendations",
        "manager_notifications"
      ]
    }
  ],
  "workflow": [
    {
      "step": 1,
      "from": "audit_agent",
      "to": "opportunity_agent"
    },
    {
      "step": 2,
      "from": "opportunity_agent",
      "to": "reporting_agent"
    }
  ]
}
