---
swagger: "2.0"
x-collection-name: Meetup
x-complete: 0
info:
  title: Meetup Event Payments
  description: Allows organizers of a group to note payments made by members for an
    event. This is the 'Mark Paid' feature seen in the RSVP listings on event details
    pages and affects the 'pay_status' response fields in [2/rsvps](/meetup_api/docs/2/rsvps/#response)
    for paid events
  version: 1.0.0
host: api.meetup.com
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /:urlname:
    post:
      summary: Group Edit
      description: Allows organizers to edit their Meetup group information. To change
        group topics, see the [add](/meetup_api/docs/:urlname/topics/#add) and [remove](/meetup_api/docs/:urlname/topics/#remove)
        topics endpoints. To change group photo use the [Group photo upload](/meetup_api/docs/2/group_photo/#create)
        endpoint. OAuth authenticated requests require an additional [group_edit](/meetup_api/auth/#oauth2-scopes)
        permission.
      operationId: groups
      x-api-path-slug: urlname-post
      parameters:
      - in: query
        name: add_topics
        description: Comma-delimited list of topic ids to associate with group
        type: string
      - in: query
        name: country
        description: The ISO_3166-1 country code for the country which contains the
          city
        type: string
      - in: query
        name: description
        description: Summary of what the Meetup group is about in simple HTML format
        type: string
      - in: query
        name: dryrun
        description: Boolean parameter that will cause this endpoint to apply all
          validation rules without actually saving changes in which case the response
          will only reflect the groups current attributes
        type: string
      - in: query
        name: ga_code
        description: Google Analytics code for group
        type: string
      - in: query
        name: join_mode
        description: Controls how members are let into the group
        type: string
      - in: query
        name: key_photo
        description: Groups primary photo
        type: string
      - in: query
        name: list_addr
        description: Mailing list prefix
        type: string
      - in: query
        name: list_mode
        description: Defines policy for who can post to the group mailing list
        type: string
      - in: query
        name: name
        description: Display name of the group
        type: string
      - in: query
        name: photo_req
        description: Indicates that a member must provide a photo before joining
        type: string
      - in: query
        name: questions_req
        description: Indicates that provided questions are required before joining
        type: string
      - in: query
        name: question_edit_{id}
        description: Edits a current profile question identified by an id in the parameter
          name
        type: string
      - in: query
        name: question_{index}
        description: A new profile question defined in the order of index provided
          in the request parameter name
        type: string
      - in: query
        name: remove_topics
        description: Comma-delimited list of topic ids to disassociate with group
        type: string
      - in: query
        name: urlname
        description: Name used for the groups web address on meetup
        type: string
      - in: query
        name: visibility
        description: Restricts group visibility for non-members
        type: string
      - in: query
        name: welcome_message
        description: Message sent to members after they join
        type: string
      - in: query
        name: who
        description: What members of the group will be called
        type: string
      - in: query
        name: zip
        description: The ZIP code of the city
        type: string
      - in: query
        name: '{service}_uri'
        description: A URI for a social network service
        type: string
      responses:
        200:
          description: OK
      tags:
      - Events
      - Groups
  /:urlname/events/:id/payments:
    post:
      summary: Event Payments
      description: Allows organizers of a group to note payments made by members for
        an event. This is the 'Mark Paid' feature seen in the RSVP listings on event
        details pages and affects the 'pay_status' response fields in [2/rsvps](/meetup_api/docs/2/rsvps/#response)
        for paid events
      operationId: events
      x-api-path-slug: urlnameeventsidpayments-post
      parameters:
      - in: query
        name: amount
        description: The monetary amount of money the member submitted
        type: string
      - in: query
        name: member
        description: Member Id of member who made a payment
        type: string
      - in: query
        name: paid_on
        description: The time the payment was made in milliseconds from the epoc
        type: string
      - in: query
        name: quantity
        description: The number of payments made
        type: string
      responses:
        200:
          description: OK
      tags:
      - Events
      - Payments
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---