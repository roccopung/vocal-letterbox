# vocal-letterbox

<b>Code used for recording + local storage through terminal:</b><br>
sudo arecord -f cd -Dhw:0 vocal-letterbox/ name of the file.wav


<b>Code used for recording file + local storage through python:</b><br>
import subprocess<br>
import os<br>
import time<br>
import signal<br>

#proc_args = ['arecord', '-D' , 'dmic_sv' , '-c2' , '-r' , '44100' , '-f' , 'S32_LE' , '-t' , 'wav' , '-V' , 'mono' , '-v' , 'subprocess1.wav']<br>
proc_args = ['arecord', '-f', 'cd', '-Dhw:0', 'vocal-letterbox/name_of_file.wav']<br>
rec_proc = subprocess.Popen(proc_args, shell=False, preexec_fn=os.setsid)<br>
print("startRecordingArecord()> rec_proc pid= " + str(rec_proc.pid))<br>
print("startRecordingArecord()> recording started")<br><br>

time.sleep(20)<br>
os.killpg(rec_proc.pid, signal.SIGTERM)<br>
rec_proc.terminate()<br>
rec_proc = None<br>
print("stopRecordingArecord()> Recording stopped")<br>

