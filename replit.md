# Shubh Game Hub - 3-Player Gaming Platform

## Overview

Shubh Game Hub is a full-stack web application designed for 3-player group gaming with real-time chat and competitive features. The platform allows users to create gaming groups, play various turn-based games, communicate through real-time chat, and track performance with leaderboards. The platform now includes comprehensive help system with FAQs and daily login rewards.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript and Vite for development/build tooling
- **UI Framework**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom dark/light theme support
- **State Management**: TanStack Query (React Query) for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Real-time Communication**: Socket.io client for WebSocket connections

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **Authentication**: Replit OAuth integration with session-based auth
- **Real-time Features**: Socket.io server for WebSocket connections
- **API Design**: RESTful endpoints with typed route handlers

### Database Architecture
- **Primary Database**: PostgreSQL (via Neon serverless)
- **ORM**: Drizzle ORM with Zod schema validation
- **Session Storage**: PostgreSQL sessions table (connect-pg-simple)
- **Migration Strategy**: Drizzle Kit for schema migrations

## Key Components

### Authentication System
- **Provider**: Replit OAuth with OpenID Connect
- **Session Management**: Express sessions stored in PostgreSQL
- **Authorization**: Middleware-based route protection
- **User Management**: Automatic user creation/updates on login

### Gaming Engine
- **Game Types**: Modular game system supporting multiple game types (Tic Tac Toe, Chess, etc.)
- **Game State**: JSON-based game state storage with real-time synchronization
- **Turn Management**: Server-side turn validation and state updates
- **3-Player Focus**: All games designed for exactly 3 players

### Real-time Communication
- **Chat System**: Group-based real-time messaging
- **Game Updates**: Live game state synchronization
- **Room Management**: Socket.io rooms for group isolation
- **Presence**: Connection status tracking

### Group Management
- **Group Creation**: Invite code-based group system
- **Member Management**: Join/leave functionality with role tracking
- **Privacy**: Groups are private and invite-only
- **Statistics**: Per-group leaderboards and player stats

## Data Flow

### Authentication Flow
1. User accesses application → Redirect to Replit OAuth if not authenticated
2. OAuth callback → Create/update user record → Establish session
3. Client receives user data → Enable authenticated features

### Game Flow
1. User selects game in group → Create game record with initial state
2. Players join game → Real-time participant updates via WebSocket
3. Player makes move → Validate on server → Update game state → Broadcast to all players
4. Game completion → Update player statistics → Show winner modal

### Chat Flow
1. User sends message → Validate and store in database
2. Broadcast message to all group members via WebSocket
3. Real-time message display with user information

## External Dependencies

### Core Infrastructure
- **Replit Platform**: Hosting, authentication, and development environment
- **Neon Database**: Serverless PostgreSQL hosting
- **Socket.io**: Real-time bidirectional communication

### UI/UX Libraries
- **Radix UI**: Accessible component primitives
- **Tailwind CSS**: Utility-first styling framework
- **Lucide React**: Icon library
- **React Hook Form**: Form handling and validation

### Development Tools
- **Vite**: Fast development server and build tool
- **TypeScript**: Type safety and developer experience
- **ESLint/Prettier**: Code quality and formatting

## Deployment Strategy

### Development Environment
- **Platform**: Replit with hot reloading via Vite
- **Database**: Shared Neon database with development schema
- **Real-time**: Socket.io with development CORS settings

### Production Considerations
- **Build Process**: Vite production build with static asset optimization
- **Server Deployment**: Express server with production middleware
- **Database**: Production Neon database with connection pooling
- **Environment Variables**: Secure handling of OAuth secrets and database credentials

## Recent Changes (January 2025)

- **Rebranding**: Updated from "GameHub" to "Shubh Game Hub" across all components
- **Help System**: Added comprehensive help modal with FAQs, troubleshooting guides, and contact support
- **Daily Login Rewards**: Implemented reward system with XP points and game tokens
- **Enhanced UX**: Added floating help buttons on landing and dashboard pages
- **Support Features**: Integrated contact forms and quick support options

### Key Architectural Decisions

1. **3-Player Constraint**: Designed specifically for 3-player groups to create intimate gaming experiences
2. **Real-time First**: Socket.io integration for immediate game updates and chat
3. **Session-based Auth**: Leverages Replit's OAuth for seamless user experience
4. **PostgreSQL Choice**: Relational database for complex gaming relationships and statistics
5. **Component Architecture**: Modular React components with shadcn/ui for consistency
6. **Type Safety**: Full TypeScript implementation across frontend and backend
7. **Help-First Design**: Integrated help system accessible from every page with comprehensive support