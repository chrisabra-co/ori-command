# ORI (Optimize-Research-Implement) for Claude Code

A powerful slash command for Claude Code that executes autonomous multi-phase workflows for complex software engineering tasks. Based on the ORI framework with intelligent model selection, quality gates, and comprehensive error handling.

## Features

- **Multi-Phase Workflow** - 5 phases from strategy to documentation
- **Intelligent Model Selection** - Automatic selection of Opus/Sonnet/Haiku based on complexity
- **Deep Research** - Web search, documentation analysis, codebase examination
- **Security Verification** - OWASP Top 10 checks, vulnerability assessment
- **Quality Gates** - Validation between each phase ensures high-quality output
- **Error Recovery** - Automatic rollback and alternative approaches
- **Context Preservation** - Handoff packets maintain full context between phases
- **Zero Setup** - Works immediately as a slash command

## What is ORI?

ORI is a structured workflow framework that breaks down complex tasks into manageable phases:

```
Phase 0: STRATEGY    → Analyze task, design research plan
Phase 1: RESEARCH    → Deep dive into docs, examples, best practices
Phase 2: VERIFY      → Cross-validate, security review, feasibility check
Phase 3: IMPLEMENT   → Execute solution with tests and error handling
Phase 4: DOCUMENT    → Update README, CHANGELOG, create summary
```

Each phase uses the optimal AI model:
- **Opus** for complex reasoning and strategic planning
- **Sonnet** for balanced implementation and verification
- **Haiku** for fast documentation updates

## Installation

### Quick Install (Recommended)

1. Download the command file:
```bash
curl -o ~/.claude/commands/ori.md \
  https://raw.githubusercontent.com/chrisabra-co/ori-command/main/.claude/commands/ori.md
```

2. Restart Claude Code

3. The `/ori` command is now available globally!

### Manual Install

1. Clone the repository:
```bash
git clone https://github.com/chrisabra-co/ori-command.git
cd ori-command
```

2. Copy the command to your Claude Code configuration:
```bash
mkdir -p ~/.claude/commands
cp .claude/commands/ori.md ~/.claude/commands/
```

3. Restart Claude Code

## Usage

### Basic Usage

```bash
# Execute any complex task
/ori [your task description]

# Examples
/ori implement JWT authentication for the Express API
/ori add rate limiting to all API endpoints
/ori refactor the user service to use dependency injection
/ori optimize database queries in the analytics module
```

### Example Workflow

**Input:**
```bash
/ori implement JWT authentication for Express API with refresh tokens
```

**Phase 0: Strategy (Opus)**
- Analyzes task complexity: HIGH
- Domain: Backend/Security
- Risk flags: security, authentication
- Recommends: Opus for research, Sonnet for implementation
- Designs research strategy with 5 key questions

**Phase 1: Research (Opus - complex task)**
- Searches official JWT documentation
- Reviews Express authentication patterns
- Finds refresh token implementation examples
- Examines security best practices (OWASP)
- Identifies required packages: jsonwebtoken, bcrypt

**Phase 2: Verification (Sonnet)**
- Cross-validates JWT approach is current
- Security review:
  - Token storage (httpOnly cookies)
  - Secret management (environment variables)
  - Token expiration (access: 15min, refresh: 7days)
  - Refresh token rotation
- Performance: Minimal impact
- Decision: APPROVED with security enhancements

**Phase 3: Implementation (Sonnet)**
- Creates auth middleware
- Implements login/refresh endpoints
- Adds token generation/validation
- Writes comprehensive tests
- Includes error handling and logging

**Phase 4: Documentation (Haiku)**
- Updates README with auth setup
- Adds CHANGELOG entry
- Creates usage examples
- Documents environment variables

**Result:**
Complete JWT authentication system with refresh tokens, security best practices, tests, and documentation.

## How It Works

### Phase 0: Research Strategy (Opus)

Analyzes your request to understand:
- **Complexity**: LOW/MEDIUM/HIGH
- **Domain**: Code, data, infrastructure, UX, etc.
- **Novelty**: Established pattern vs. new problem
- **Risk Flags**: Security, privacy, compliance concerns

Designs optimal research strategy:
- Primary questions to answer
- Information sources to consult
- Search queries to execute
- Validation criteria

Selects models for each phase based on complexity.

### Phase 1: Deep Research (Dynamic)

Gathers comprehensive information:
- **Web Search**: Latest documentation, best practices
- **Code Examples**: GitHub patterns, working implementations
- **Codebase Analysis**: Existing patterns, related components
- **Synthesis**: Best approach, alternatives, assumptions

Uses Opus for complex/novel tasks, Sonnet for standard tasks.

### Phase 2: Verification (Sonnet)

Validates research findings:
- **Cross-Validation**: Confirm approach is current
- **Security Review**: OWASP Top 10, vulnerabilities
- **Performance**: Scalability, bottlenecks
- **Feasibility**: Dependencies, compatibility, complexity

Makes final decision on approach.

### Phase 3: Implementation (Sonnet/Haiku)

Executes the solution:
- **Safety First**: Git check, backup, branch creation
- **Implementation**: Step-by-step with validation
- **Testing**: Unit tests, integration tests, edge cases
- **Error Handling**: Automatic recovery or rollback

Uses Sonnet for complex code, Haiku for simple edits.

### Phase 4: Documentation (Haiku)

Updates all documentation:
- **README**: Feature docs, setup, usage examples
- **CHANGELOG**: Version entry, changes, breaking changes
- **Summary**: Implementation report, next steps
- **Comments**: Inline documentation, TODOs

## Quality Gates

Each phase must pass validation before proceeding:

**Phase 0 → 1:**
- Complete strategy
- Risk flags identified
- Model selection justified

**Phase 1 → 2:**
- Minimum 2 sources consulted
- Primary approach identified
- Assumptions documented

**Phase 2 → 3:**
- Security review passed
- No critical blockers
- Clear implementation plan

**Phase 3 → 4:**
- Core implementation complete
- Critical tests passing
- No unresolved errors

## Model Selection Logic

### When to Use Opus
- Strategic planning and research design
- Complex multi-step reasoning
- Novel or ambiguous problems
- High-stakes architectural decisions

### When to Use Sonnet
- Most implementation tasks
- Code generation and refactoring
- Validation and verification
- Balanced performance/cost

### When to Use Haiku
- Simple file edits
- Documentation updates
- Formatting and style fixes
- Quick, straightforward tasks

## Benefits

- **Comprehensive Solutions** - Nothing overlooked, all aspects covered
- **Security First** - Automatic security review on all implementations
- **Best Practices** - Research ensures current, recommended approaches
- **Cost Optimized** - Intelligent model selection minimizes cost
- **Quality Assured** - Multi-phase validation and quality gates
- **Error Resilient** - Automatic recovery and rollback strategies
- **Well Documented** - Complete documentation updates included
- **Learning Tool** - See expert workflow for complex tasks

## When to Use ORI

**Best For:**
- Complex features requiring research
- Security-sensitive implementations
- New technology/framework adoption
- Architectural changes
- Performance optimization
- Multi-component integrations

**Not Needed For:**
- Simple bug fixes
- Trivial edits
- Well-understood tasks
- Quick experiments

## Example Use Cases

### Authentication Implementation
```bash
/ori implement OAuth2 authentication with Google provider
```

### Performance Optimization
```bash
/ori optimize the dashboard query that's taking 5+ seconds
```

### Feature Addition
```bash
/ori add real-time notifications using WebSockets
```

### Security Hardening
```bash
/ori add rate limiting and request validation to all API endpoints
```

### Architecture Refactoring
```bash
/ori refactor the monolith to microservices starting with user service
```

## Configuration

The ORI command is self-contained and requires no configuration. However, you can customize behavior by:

1. **Model Overrides** - Edit `.claude/commands/ori.md` to change model selections
2. **Phase Customization** - Adjust research depth, verification criteria
3. **Quality Gates** - Modify validation requirements between phases

## Comparison with MCP Server

### Slash Command Version (This Project)
- ✅ Zero setup, works immediately
- ✅ No separate server process
- ✅ Lightweight and fast
- ✅ Perfect for Claude Code users
- ❌ No persistent logging
- ❌ No programmatic API access

### MCP Server Version
- ✅ Persistent execution logs
- ✅ Programmatic tool access
- ✅ SME quality gate agents
- ✅ Configurable workflows
- ❌ Requires MCP setup
- ❌ Additional complexity

## Troubleshooting

### Command Not Found
- Ensure file is at `~/.claude/commands/ori.md`
- Restart Claude Code completely
- Check file permissions (should be readable)

### Phase Failures
- Review error messages in output
- Check if quality gates were met
- Verify required tools available (git, etc.)

### Model Selection Issues
- Phase 0 may select different model than expected
- This is intentional based on complexity analysis
- Trust the strategic analysis

## Contributing

Contributions welcome! Areas for improvement:

- Additional domain-specific research strategies
- More sophisticated model selection criteria
- Enhanced security verification rules
- Extended quality gate validations
- Custom phase templates

## License

MIT License - see [LICENSE](LICENSE) file for details

## Credits

Based on the [MCP Server ORI](https://github.com/grandinh/mcp-server-ori) by Harrison Grandin. This slash command version was adapted for Claude Code to provide a lightweight, zero-setup implementation of the ORI workflow framework.

Special thanks to Harrison Grandin for the original ORI framework and workflow design.

## Support

- **Issues**: [GitHub Issues](https://github.com/chrisabra-co/ori-command/issues)
- **Original Framework**: [MCP Server ORI](https://github.com/grandinh/mcp-server-ori)
- **Documentation**: See the command file for complete workflow details

---

**Made for complex software engineering tasks with Claude Code**