t = readtable("data/g_edges.csv");
names = unique([string(t.Source);string(t.Target)]);
gr = zeros(length(names),length(names));
m = containers.Map(names, 1:size(names));
targs = string(t.Target)';
srcs = string(t.Source)';
for i = 1:length(t.Target)
    gr(m(srcs(i)),m(targs(i))) = gr(m(srcs(i)),m(targs(i)))+1;
end
s = zeros(1,length(srcs));
tt = zeros(1,length(srcs));
for i = 1:length(srcs)
    s(i) = m(srcs(i));
    tt(i) = m(targs(i));
end
deg = sum(gr);
sizes = 2*sqrt(deg-min(deg))+0.2;
colors = [sizes/max(sizes)';zeros(1,length(sizes));1 - sizes/max(sizes)'];
weights = double(t.Weight);
g = digraph(s,tt,weights');
plot(g, 'MarkerSize',sizes, 'NodeColor', colors')
colormap([linspace(0,1,256); zeros(1,256); linspace(1,0,256)]')
colorbar 
caxis([min(sizes), max(sizes)])


sixth = sort(sum(gr));
sixth = sixth(1,length(sixth)-5);
disp("Top 5")
disp(names(flip(find(sum(gr) > sixth))))


for i = shortestpath(g, m("NED"), m("TYRION"))
    disp(names(i))
end
