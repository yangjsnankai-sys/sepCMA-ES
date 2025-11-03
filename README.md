## Sep-CMA-ES Optimization Framework for Simulink Models

### Overview
This code implements an advanced **sep-CMA-ES (Separable Covariance Matrix Adaptation Evolution Strategy)** optimization framework with hybrid local search, specifically designed for efficient parameter tuning in Simulink models. The provided **parafoil controller model** has been fully processed and serves as a ready-to-use template.

### Performance Advantage
- **Faster Convergence**: sep-CMA-ES converges significantly quicker than standard CMA-ES
- **Reduced Computation Time**: Diagonal covariance matrix reduces computational complexity
- **Hybrid Optimization**: Combines global search with local fminbnd refinement
- **Efficient Resource Usage**: Optimized for shorter runtime while maintaining solution quality

### File Structure
- **`sep()`** - Main optimization driver (sep-CMA-ES + hybrid local search)
- **`parafoil2.slx`** - Pre-processed Simulink template (parafoil controller model)

### Key Features
- **Separable CMA-ES**: Diagonal covariance matrix for faster adaptation
- **Parallel Evaluation**: MATLAB parallel computing for population evaluation
- **Intelligent Caching**: Avoids redundant simulations through result caching
- **Noise Reduction**: Multiple repetitions with median aggregation
- **Hybrid Approach**: Global sep-CMA-ES followed by local fminbnd optimization

### Quick Start
1. **Model Integration**: Replace the pre-processed `parafoil2.slx` with your own Simulink model
2. **Parameter Setup**: Ensure your model has tunable parameters (like `height_action`)
3. **Output Configuration**: Model must output evaluation signals (like `episodeReward`)
4. **Run Optimization**: Simply execute `sep()` - the framework handles everything automatically

### Default Configuration
- **Search Range**: 3.0-20.0 meters with 0.2m quantization
- **Optimization**: 12 population size, 200 maximum evaluations
- **Noise Handling**: 5 simulation repetitions per candidate
- **Output**: Optimal parameters, performance metrics, and complete results (`sep_out.mat`)
