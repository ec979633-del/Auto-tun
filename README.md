# Auto-tun
vocal tun

#pragma once

#include <JuceHeader.h>

class EBTUNEAdvancedAudioProcessor
    : public juce::AudioProcessor
{
public:
    EBTUNEAdvancedAudioProcessor();
    ~EBTUNEAdvancedAudioProcessor() override = default;

    void prepareToPlay(double sampleRate,
                       int samplesPerBlock) override;

    void releaseResources() override;

    void processBlock(juce::AudioBuffer<float>&,
                      juce::MidiBuffer&) override;

    juce::AudioProcessorEditor* createEditor() override;
    bool hasEditor() const override { return true; }

    const juce::String getName() const override
    {
        return "EB TUNE Advanced";
    }

    bool acceptsMidi() const override { return false; }
    bool producesMidi() const override { return false; }
    bool isMidiEffect() const override { return false; }

    double getTailLengthSeconds() const override
    {
        return 0.0;
    }

    int getNumPrograms() override { return 1; }
    int getCurrentProgram() override { return 0; }
    void setCurrentProgram(int) override {}
    const juce::String getProgramName(int) override
    {
        return {};
    }
    void changeProgramName(int, const juce::String&) override {}

    void getStateInformation(
        juce::MemoryBlock& destinationData) override;

    void setStateInformation(
        const void* data, int sizeInBytes) override;

    using Parameters =
        juce::AudioProcessorValueTreeState;

    Parameters parameters;

private:
    JUCE_DECLARE_NON_COPYABLE_WITH_LEAK_DETECTOR(
        EBTUNEAdvancedAudioProcessor)
};
