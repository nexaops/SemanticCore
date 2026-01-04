# Contributing to PgVector E-commerce Demo

Thank you for your interest in contributing to this research and educational project! We welcome contributions from researchers, students, developers, and anyone interested in advancing semantic search and vector database technologies.

## 🎯 Types of Contributions

### 🔬 Research Contributions
- **New Embedding Strategies**: Alternative approaches to dual embeddings
- **Search Algorithms**: Improved ranking, fusion, and similarity techniques
- **Performance Studies**: Benchmarking and optimization research
- **Evaluation Metrics**: New methods for measuring search quality and relevance
- **Academic Papers**: Research using this codebase (please cite us!)

### 💻 Technical Contributions
- **Bug Fixes**: Issues with search, database operations, or UI
- **Feature Enhancements**: New search capabilities or user interface improvements
- **Performance Optimizations**: Database queries, indexing, or algorithm improvements
- **Documentation**: Tutorials, examples, API documentation, or educational content
- **Testing**: Unit tests, integration tests, or performance benchmarks

### 📊 Data Contributions
- **New Datasets**: Additional product categories or data sources
- **Data Quality**: Improvements to data cleaning and processing
- **Analysis Tools**: New Jupyter notebooks or analysis scripts
- **Benchmarks**: Performance baselines and comparison studies



## 📋 Contribution Process

### 1. Before You Start
- **Check Issues**: Look for existing issues or discussions
- **Create Issue**: For new features or bugs, create an issue first
- **Discuss Approach**: For major changes, discuss your approach in the issue

### 2. Development Workflow
```bash
# Create a feature branch
git checkout -b feature/your-feature-name

# Make your changes
# ... code, test, document ...

# Commit with clear messages
git commit -m "Add semantic search improvement for multi-word queries"

# Push and create pull request
git push origin feature/your-feature-name
```

### 3. Pull Request Guidelines
- **Clear Title**: Descriptive title explaining the change
- **Detailed Description**: What, why, and how of your changes
- **Testing**: Include tests or explain how you tested
- **Documentation**: Update relevant documentation
- **Research Context**: For algorithm changes, explain the research basis

## 🧪 Testing Guidelines

### Backend Testing
```bash
# Run existing tests (when available)
cd backend
python -m pytest

# Test search functionality
python -c "
import asyncio
from app.core.database import AsyncSessionLocal
from app.services.search_service import SearchService

async def test_search():
    async with AsyncSessionLocal() as db:
        results, _ = await SearchService.search_products(db, 'baby toys', limit=5)
        print(f'Found {len(results)} results')

asyncio.run(test_search())
"
```

### Performance Testing
```bash
# Test database performance
docker exec -it demo_db psql -U user -d ecommerce_vector_db -c "
EXPLAIN (ANALYZE, BUFFERS) 
SELECT * FROM products 
ORDER BY embedding_semantic <-> '[0.1,0.2,...]' 
LIMIT 10;
"
```

## 📚 Code Style Guidelines

### Python (Backend)
- **Type Hints**: Always include comprehensive type annotations
- **Docstrings**: Use detailed docstrings with algorithm explanations
- **Async/Await**: Use async patterns for database operations
- **Error Handling**: Proper exception handling and logging

```python
async def search_products(
    db: AsyncSession,
    query: str,
    limit: int = 20
) -> tuple[List[Product], Optional[Dict[str, Any]]]:
    """
    Perform semantic search with detailed algorithm explanation.
    
    Args:
        db: Database session for queries
        query: Natural language search query
        limit: Maximum number of results to return
        
    Returns:
        Tuple of (products, facets) for search results
        
    Algorithm:
        1. Generate query embedding using sentence transformer
        2. Perform vector similarity search with HNSW index
        3. Apply keyword matching with word boundaries
        4. Combine results using enhanced RRF fusion
    """
```

### Documentation
- **Clear Explanations**: Write for educational purposes
- **Code Examples**: Include practical examples
- **Research Context**: Explain the "why" behind decisions
- **Mathematical Formulations**: Include formulas when relevant

## 🔬 Research Contribution Guidelines

### Algorithm Improvements
- **Baseline Comparison**: Compare against existing implementation
- **Performance Metrics**: Include speed and accuracy measurements
- **Research Citations**: Reference relevant academic papers
- **Reproducibility**: Ensure results can be reproduced

### Data Analysis
- **Statistical Significance**: Use proper statistical methods
- **Visualization**: Include clear charts and graphs
- **Interpretation**: Explain what the results mean
- **Limitations**: Discuss limitations and future work

### Documentation Standards
- **Mathematical Notation**: Use clear mathematical formulations
- **Algorithm Descriptions**: Step-by-step explanations
- **Complexity Analysis**: Time and space complexity when relevant
- **Use Cases**: Practical applications and examples

## 🐛 Bug Reports

### Information to Include
- **Environment**: OS, Docker version, browser (for frontend issues)
- **Steps to Reproduce**: Clear, numbered steps
- **Expected Behavior**: What should happen
- **Actual Behavior**: What actually happens
- **Logs**: Relevant error messages or logs
- **Data**: Sample queries or data that cause issues

### Example Bug Report
```markdown
**Bug**: Search returns no results for valid queries

**Environment**: 
- OS: macOS 13.0
- Docker: 24.0.6
- Browser: Chrome 120.0

**Steps to Reproduce**:
1. Start application with `docker-compose up`
2. Navigate to http://localhost:3000
3. Search for "baby toys"
4. No results appear

**Expected**: Should return toy products for babies
**Actual**: Empty results page
**Logs**: See attached backend logs showing SQL errors
```

## 📈 Performance Contributions

### Benchmarking
- **Baseline Measurements**: Document current performance
- **Test Methodology**: Explain how you measured improvements
- **Hardware Specs**: Include system specifications
- **Reproducible Tests**: Provide scripts for others to run

### Optimization Areas
- **Database Queries**: SQL optimization and indexing
- **Vector Operations**: HNSW parameter tuning
- **Embedding Generation**: Parallel processing improvements
- **Frontend Performance**: React optimization and caching

## 🎓 Educational Contributions

### Tutorials and Guides
- **Step-by-Step Tutorials**: Beginner-friendly explanations
- **Advanced Topics**: Deep dives into algorithms and theory
- **Use Case Examples**: Real-world applications
- **Troubleshooting Guides**: Common issues and solutions

### Code Comments and Documentation
- **Inline Comments**: Explain complex algorithms
- **Function Documentation**: Comprehensive docstrings
- **Architecture Explanations**: High-level system design
- **Research References**: Links to relevant papers

## 🤝 Community Guidelines

### Communication
- **Be Respectful**: Treat all contributors with respect
- **Be Constructive**: Provide helpful feedback and suggestions
- **Be Patient**: Remember this is an educational project
- **Be Inclusive**: Welcome contributors of all skill levels

### Code Review Process
- **Thorough Reviews**: Take time to understand changes
- **Educational Focus**: Explain suggestions and alternatives
- **Research Discussion**: Discuss algorithmic choices
- **Collaborative Improvement**: Work together to improve code

## 📞 Getting Help

### Where to Ask Questions
- **GitHub Issues**: For bugs and feature requests
- **GitHub Discussions**: For general questions and research discussions
- **Code Comments**: For specific implementation questions
- **Documentation**: Check existing docs first

### Response Times
- **Issues**: We aim to respond within 48 hours
- **Pull Requests**: Initial review within 1 week
- **Discussions**: Community-driven, varies by topic

## 🏆 Recognition

### Contributors
- All contributors will be listed in the project README
- Significant contributions will be highlighted in release notes
- Research contributions may be cited in academic contexts

### Attribution
- **Code Contributions**: Git history provides automatic attribution
- **Research Ideas**: Acknowledged in documentation and papers
- **Bug Reports**: Credited in issue resolution
- **Documentation**: Bylines on major documentation contributions

---

Thank you for contributing to the advancement of semantic search and vector database research! Your contributions help make this technology more accessible to researchers, students, and developers worldwide.

**Questions?** Feel free to open an issue or start a discussion. We're here to help! 🚀