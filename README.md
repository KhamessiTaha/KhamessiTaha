import React, { useState } from 'react';
import { 
  Code, 
  Rocket, 
  Brain, 
  Globe, 
  Star, 
  Award 
} from 'lucide-react';

const ProfileHighlights = () => {
  const [activeSkill, setActiveSkill] = useState(null);

  const skillHighlights = {
    'Space Technology': {
      description: "Pioneering cosmic exploration through innovative web technologies",
      icon: <Rocket color="#00C9FF" size={48} />
    },
    'Machine Learning': {
      description: "Transforming complex data into intelligent solutions",
      icon: <Brain color="#92FE9D" size={48} />
    },
    'Full Stack Development': {
      description: "Crafting seamless digital experiences from frontend to backend",
      icon: <Code color="#00C9FF" size={48} />
    }
  };

  return (
    <div className="bg-black/70 p-6 rounded-lg text-white">
      <h2 className="text-2xl font-bold mb-4 text-center flex items-center justify-center">
        <Globe className="mr-2" /> Tech Exploration Highlights
      </h2>
      <div className="grid grid-cols-3 gap-4">
        {Object.entries(skillHighlights).map(([skill, details]) => (
          <div 
            key={skill} 
            className={`p-4 text-center transition-all duration-300 rounded-lg cursor-pointer 
              ${activeSkill === skill 
                ? 'bg-blue-600/50 scale-105' 
                : 'hover:bg-blue-500/30'}`}
            onClick={() => setActiveSkill(activeSkill === skill ? null : skill)}
          >
            <div className="flex justify-center mb-2">{details.icon}</div>
            <h3 className="font-semibold text-lg">{skill}</h3>
            {activeSkill === skill && (
              <p className="mt-2 text-sm">{details.description}</p>
            )}
          </div>
        ))}
      </div>
      <div className="mt-4 text-center flex justify-center items-center">
        <Award className="mr-2" /> 
        <span className="text-sm font-light">2024 NASA Space Apps Challenge Global Nominee</span>
      </div>
    </div>
  );
};

export default ProfileHighlights;
