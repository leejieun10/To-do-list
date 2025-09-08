# Technical Specification Document

## Overview
This document outlines the technical guidelines and best practices for development work in this project. It serves as a comprehensive reference for maintaining code quality, design consistency, and proper development workflows.

## 1. Planning and Development Process

### 1.1 Thinking Process
- Use `<Thinking>` tags to plan changes before implementation
- Refer to the Alignment section to understand when to launch tasks
- Consider the appropriate response approach for different types of user queries

### 1.2 Task Management
- Launch appropriate tasks based on the complexity and scope of the request
- Use SearchRepo or ReadFile to understand codebase before making changes
- Follow Todo List Guidelines for complex multi-step projects
- Do NOT break up single apps or pages into multiple tasks

## 2. Design Guidelines

### 2.1 Design Inspiration
- Utilize the GenerateDesignInspiration subagent for design inspiration when needed
- Ensure designs are visually appealing and meet user requirements

### 2.2 Color Selection
- Think through correct color selection for the project theme
- Maintain consistency across the application

### 2.3 Typography
- Follow typography best practices
- Ensure readability and visual hierarchy

### 2.4 Layout Method Priority
Use the following layout methods in order of preference:
1. **Flexbox** - For most layouts and component arrangements
2. **CSS Grid** - For complex 2D layouts when flexbox is insufficient
3. **Other methods** - Only when absolutely necessary

## 3. File Editing Guidelines

### 3.1 File Reading Requirements
- **MUST** use SearchRepo or ReadFile to read files before editing them
- Never assume file contents without verification
- Understand existing implementation before making changes

### 3.2 Editing Best Practices
- Only edit files that need to be changed
- Use my ability to quickly edit aggressively to skip unchanged code
- Do NOT write variations like "... existing header ..." or "... unchanged code ..."

### 3.3 Change Documentation
- Add surrounding comments to explain changes, especially if not obvious
- Use Change Comment format: `// ` followed by brief description of the change
- Example: `// Updated button color to match brand guidelines`

### 3.4 Debugging Guidelines
- Use `console.log("[v0] ...")` statements for debugging
- Include relevant context in debug messages
- Remove debug statements after debugging is complete using commentss

## 4. Code Quality Standards

### 4.1 Code Structure
- Maintain clean, readable code structure
- Follow established patterns in the codebase
- Ensure proper component organization

### 4.2 Comments and Documentation
- Provide clear comments for complex logic
- Document changes and their reasoning
- Maintain up-to-date documentation

## 5. Response Guidelines

### 5.1 Communication Style
- Do not use emojis unless explicitly requested
- Maintain professional and clear communication
- Focus on technical accuracy and clarity

### 5.2 Response Format
- Write a postamble explaining code or summarizing changes
- Limit postamble to 2-4 sentences maximum
- Never write more than a paragraph unless explicitly asked

### 5.3 Content Guidelines
- Provide comprehensive but concise explanations
- Focus on actionable information
- Ensure responses are helpful and relevant

## 6. Project-Specific Requirements

### 6.1 Technology Stack
- Next.js with App Router
- TypeScript for type safety
- Tailwind CSS for styling
- shadcn/ui component library

### 6.2 File Structure
- Follow established project structure
- Maintain consistency with existing patterns
- Use appropriate file naming conventions

### 6.3 Dependencies
- Utilize existing project dependencies
- Follow established patterns for new additions
- Ensure compatibility with current stack

## 7. Quality Assurance

### 7.1 Testing Approach
- Verify changes work as expected
- Test responsive design and accessibility
- Ensure cross-browser compatibility

### 7.2 Performance Considerations
- Optimize for performance where possible
- Follow best practices for loading and rendering
- Consider mobile and desktop experiences

## 8. Maintenance and Updates

### 8.1 Code Maintenance
- Keep code clean and well-organized
- Regular refactoring when beneficial
- Maintain consistent coding standards

### 8.2 Documentation Updates
- Keep documentation current with code changes
- Update specifications when processes change
- Ensure team alignment on standards

---

**Document Version**: 1.0  
**Last Updated**: Current Session  
**Maintained By**: Development Team
