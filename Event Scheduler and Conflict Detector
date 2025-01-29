from datetime import datetime, timedelta

def parse_time(time_str):
    """Convert time in HH:MM format to a datetime object."""
    return datetime.strptime(time_str, "%H:%M")

def format_time(time_obj):
    """Convert a datetime object to time in HH:MM format."""
    return time_obj.strftime("%H:%M")

def detect_conflicts(events):
    """Detect conflicts between events."""
    conflicts = []
    for i in range(len(events)):
        for j in range(i + 1, len(events)):
            if events[i]["end"] > events[j]["start"] and events[i]["start"] < events[j]["end"]:
                conflicts.append((events[i]["name"], events[j]["name"]))
    return conflicts

def suggest_resolutions(events, conflicts):
    """Suggest resolutions for conflicting events."""
    resolutions = []
    for conflict in conflicts:
        event1 = next(e for e in events if e["name"] == conflict[0])
        event2 = next(e for e in events if e["name"] == conflict[1])

        # Suggest moving event2 to after event1 ends
        new_start = event1["end"]
        new_end = new_start + (event2["end"] - event2["start"])
        resolutions.append(f"Reschedule '{event2['name']}' to Start: '{format_time(new_start)}', End: '{format_time(new_end)}'")
    return resolutions

def main():
    # Example input
    events = [
        {"name": "Meeting A", "start": parse_time("09:00"), "end": parse_time("10:30")},
        {"name": "Workshop B", "start": parse_time("10:00"), "end": parse_time("11:30")},
        {"name": "Lunch Break", "start": parse_time("12:00"), "end": parse_time("13:00")},
        {"name": "Presentation C", "start": parse_time("10:30"), "end": parse_time("12:00")},
    ]

    # Sort events by start time
    events.sort(key=lambda x: x["start"])

    # Detect conflicts
    conflicts = detect_conflicts(events)

    # Suggest resolutions
    resolutions = suggest_resolutions(events, conflicts)

    # Output the results
    print("Sorted Schedule:")
    for event in events:
        print(f"- {event['name']}, Start: '{format_time(event['start'])}', End: '{format_time(event['end'])}'")

    print("\nConflicting Events:")
    for conflict in conflicts:
        print(f"- {conflict[0]} and {conflict[1]}")

    print("\nSuggested Resolutions:")
    for resolution in resolutions:
        print(f"- {resolution}")

if __name__ == "__main__":
    main()
