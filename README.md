# This file and it's contents will be updated for each day during which testing occured.

# 13.04.26

# Algorithm :

1. Linear Interpolation Smoothing.
2. Per-entity based curve system, changes if the closest entity to crosshair changes.
3. Per-frame delta based noise system, applied to delta directly.
4. Per-entity based aimbot strength variance

# Code snippets (scaling reminders)

# 1.1 :

float SmoothPitch = localviewangles.X + (noisyPitchDiff * deltaTime * pitchStrength); // same applied to Yaw

# 2.1 & 4.1 :

            if (ClosestEnemyToCrosshairPtr != lastTargetPtr)
            {
                lastTargetPtr = ClosestEnemyToCrosshairPtr;
                yawVariance = randomFloat(overlay.AimbotCurveXMin, overlay.AimbotCurveXMax);
                pitchVariance = randomFloat(overlay.AimbotCurveYMin, overlay.AimbotCurveYMax);
                variance = randomFloat(-0.5f, 0.5f);
            }

# 3.1 : 
float noiseScale = 0.002f + (float)Math.Pow(deltaNormalized, 0.2f) * 0.40f;

float noisyYawDiff = YawDifferenceFinal + randomFloat(-1f, 1f) * noiseScale;
float noisyPitchDiff = PitchDifferenceFinal + randomFloat(-0.60f, 0.60f) * noiseScale;

# Results

Results are not valuable, as I did not anticipate to actually collect proper data etc. 
VACnet did not trigger during my first game, where I was using decently smooth aimbot, unfortunately I cannot remember the exact value. 
I then got bored and lowered my smoothing all the way down to 0.077, which is way too consistant and unrealistic, VACnet triggered on the 17th round.
