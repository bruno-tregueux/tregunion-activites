[activites.html](https://github.com/user-attachments/files/26529784/activites.html)
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>Treg'Union - On se ferait pas un... ?</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { font-family: 'Segoe UI', Roboto, sans-serif; background: linear-gradient(135deg, #f5f7fa 0%, #e9ecef 100%); min-height: 100vh; padding: 20px; }
        .container { max-width: 800px; margin: 0 auto; }
        .page { display: none; animation: fadeIn 0.3s ease; }
        .page.active { display: block; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
        h1 { text-align: center; background: linear-gradient(135deg, #2c5f2d 0%, #1e3a1e 100%); color: white; padding: 20px; border-radius: 60px; margin-bottom: 30px; font-size: 1.8rem; }
        .visit-counter { text-align: center; margin-bottom: 15px; color: #666; font-size: 0.9rem; }
        .visit-counter span { background: white; padding: 5px 15px; border-radius: 20px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); font-weight: bold; color: #2c5f2d; }
        .refresh-btn { margin-left: 15px; background: #2c5f2d; color: white; border: none; border-radius: 20px; padding: 5px 12px; cursor: pointer; font-size: 0.9rem; }
        .refresh-btn:hover { background: #1e3a1e; }
        .buttons-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 20px; }
        .activity-btn { display: flex; flex-direction: column; align-items: center; justify-content: center; background: white; border-radius: 50px; padding: 25px 10px; font-weight: bold; cursor: pointer; border: none; box-shadow: 0 8px 20px rgba(0,0,0,0.1); position: relative; transition: transform 0.2s; }
        .activity-btn:hover { transform: scale(1.02); }
        .btn-icon { font-size: 3.5rem; margin-bottom: 12px; }
        .btn-name { font-size: 1.1rem; text-align: center; }
        .btn-badge { position: absolute; top: 10px; right: 10px; background: #e53935; color: white; border-radius: 50%; width: 24px; height: 24px; font-size: 0.75rem; display: flex; align-items: center; justify-content: center; font-weight: bold; }
        .activity-container { background: white; padding: 25px; border-radius: 35px; box-shadow: 0 10px 30px rgba(0,0,0,0.1); }
        button, .btn-back { background: linear-gradient(135deg, #2e7d32 0%, #1b5e20 100%); color: white; border: none; padding: 12px 24px; border-radius: 40px; cursor: pointer; margin: 5px 5px 5px 0; font-size: 1rem; font-weight: bold; }
        .btn-back { background: #555; }
        input, select, textarea { width: 100%; padding: 12px; margin: 8px 0 15px 0; border-radius: 30px; border: 1px solid #ddd; font-size: 1rem; }
        textarea { border-radius: 20px; resize: vertical; }
        .event-card { border: 1px solid #e0e0e0; padding: 15px; margin: 15px 0; border-radius: 25px; background: #fefefe; }
        .event-card-home { border: 1px solid #e0e0e0; padding: 12px 15px; margin: 8px 0; border-radius: 20px; background: white; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 8px; cursor: pointer; transition: box-shadow 0.2s; }
        .event-card-home:hover { box-shadow: 0 4px 12px rgba(0,0,0,0.1); }
        .error { color: #d32f2f; background: #ffebee; padding: 12px; border-radius: 30px; }
        .success { color: #2e7d32; background: #e8f5e9; padding: 12px; border-radius: 30px; }
        .info { color: #1565c0; background: #e3f2fd; padding: 12px; border-radius: 30px; }
        .admin-link { text-align: center; margin-top: 30px; }
        .admin-link a { color: #888; text-decoration: none; font-size: 0.8rem; cursor: pointer; }
        .game-row { border: 1px solid #ddd; border-radius: 20px; padding: 12px; margin: 10px 0; }
        .admin-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px; flex-wrap: wrap; }
        .upcoming-section { margin-top: 30px; }
        .upcoming-title { font-size: 1.1rem; font-weight: bold; color: #444; margin-bottom: 12px; text-align: center; }
        .type-tag { display: inline-block; padding: 3px 10px; border-radius: 20px; color: white; font-size: 0.75rem; font-weight: bold; }
        .game-suggestion { padding: 10px 16px; cursor: pointer; border-bottom: 1px solid #f0f0f0; }
        .game-suggestion:hover { background: #f5f5f5; }
        .cards-game-area { background: #f9f2e0; border-radius: 20px; padding: 12px; margin: 10px 0; border-left: 5px solid #ff9800; }
        .cards-game-area strong { font-weight: bold; color: #e67e22; }
        .feedback-area { background: #e8f5e9; border-radius: 20px; padding: 15px; margin-top: 15px; border: 1px solid #a5d6a7; }
        .ambiance-buttons { display: flex; gap: 15px; justify-content: center; margin: 10px 0; }
        .ambiance-btn { font-size: 2rem; background: none; border: none; cursor: pointer; padding: 8px 15px; border-radius: 50px; transition: transform 0.2s; }
        .ambiance-btn:hover { transform: scale(1.1); background: #f0f0f0; }
        .participant-line { display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 8px; padding: 6px 0; border-bottom: 1px solid #eee; }
        .participant-actions button { background: none; border: none; font-size: 1.2rem; cursor: pointer; margin: 0 3px; padding: 4px 8px; border-radius: 20px; }
        .participant-actions button:hover { background: #f0f0f0; }
        @media (max-width: 550px) {
            .btn-name { font-size: 0.9rem; }
            .btn-icon { font-size: 2.5rem; }
            h1 { font-size: 1.4rem; }
        }
    </style>
</head>
<body>
<div class="container">
    <div id="homePage" class="page active">
        <h1>🎉 Treg'Union<br><span style="font-size:1rem;">on se ferait pas un... ?</span></h1>
        <div class="visit-counter">
            👁️ Visites : <span id="visitCount">...</span>
            <button id="refreshPageBtn" class="refresh-btn">🔄 Rafraîchir</button>
        </div>
        <div class="buttons-grid" id="buttonsContainer"></div>
        <div class="upcoming-section" id="upcomingSection"></div>
        <div class="admin-link"><a id="adminLink">🔧 Admin</a></div>
    </div>

    <div id="activityPage" class="page">
        <div class="activity-container">
            <button id="backToHome" class="btn-back">← Retour</button>
            <h1 id="pageTitle">Chargement...</h1>
            <button id="showFormBtn">✨ Proposer une sortie</button>
            <div id="form" style="display:none; margin-top:20px;">
                <div id="dynamicFields"></div>
                <label>📅 Date et heure *</label>
                <input type="datetime-local" id="datetime" required>
                <label>👥 Nombre de places max</label>
                <input type="number" id="maxParticipants" value="10">
                <label>☑️ Illimité</label>
                <input type="checkbox" id="unlimitedCheckbox">
                <label>🧑 Votre nom (prénom + initiale) *</label>
                <input type="text" id="creatorName" placeholder="Ex: Bruno D" required>
                <button id="saveBtn">✅ Créer la table</button>
                <button id="cancelBtn">❌ Annuler</button>
            </div>
            <div id="message"></div>
            <div id="eventsList"></div>
        </div>
    </div>

    <div id="adminPage" class="page">
        <div class="activity-container">
            <button id="backToHomeFromAdmin" class="btn-back">← Retour accueil</button>
            <div class="admin-header">
                <h1 style="margin:0;">🔧 Administration</h1>
                <button id="logoutAdminBtn" style="background:#d32f2f;">🚪 Déconnexion</button>
            </div>
            <div id="adminArea"></div>
        </div>
    </div>
</div>

<script type="module">
    import { createClient } from "https://esm.sh/@supabase/supabase-js@2";
    const SUPABASE_URL = "https://hgztmixwbivsknaeljct.supabase.co";
    const SUPABASE_KEY = "sb_publishable_yOrNMvxHE1TTnb8cDkZgiw_mq1xrcup";
    const sb = createClient(SUPABASE_URL, SUPABASE_KEY);

    const JEUX_BASE = [
        ["jeu0001","5 Alive","2 — 6","15 — 30","8+"],["jeu0002","6 qui Surprend !","2 — 10","45","10+"],["jeu0003","Abalone","Duo","20 — 30","7+"],["jeu0004","Akropolis","1 — 4","25","8+"],["jeu0005","Après l'orage...","1 — 5","20","6+"],["jeu0006","Arbre à Singe","2 — 4","15","3+"],["jeu0007","Ark Nova","1 — 4","90 — 150","14+"],["jeu0008","Atlantide, l'Empire Perdu","Duo","45","8+"],["jeu0009","Azul","2 — 4","30 — 45","8+"],["jeu0010","Azul - Les Vitraux de Sintra","2 — 4","30 — 60","8+"],["jeu0011","Azul - Pavillon d'Été","2 — 4","30 — 60","8+"],["jeu0012","Barbapapa Mémo","1 — 4","15","3+"],["jeu0013","Bata-Waf","2 — 4","15","3+"],["jeu0014","Belote Junior","2 — 6","30","6+"],["jeu0015","Bescherelle: Super Défi Histoire","2 — 6","10","7+"],["jeu0016","Boggle","1 — 8","30","8+"],["jeu0017","Caldera Park","1 — 4","30 — 40","10+"],["jeu0018","Carcassonne","2 — 5","35","7+"],["jeu0019","Caro Cane","2 — 4","20","4+"],["jeu0020","Chromino","1 — 8","30","6+"],["jeu0021","Clac Clac","2 — 6","10","4+"],["jeu0022","Codenames Duo","2+","15","12+"],["jeu0023","Concept - Kids Animaux","2 — 10","30","4+"],["jeu0024","Crack List","2 — 8","30","10+"],["jeu0025","Crack Word","2 — 4","30","10+"],["jeu0026","Croque-carotte","2 — 4","15 — 30","4+"],["jeu0027","Cui-cui !","2 — 4","15","3+"],["jeu0028","Detective Puzzle - The City","Solo","15 — 30","5+"],["jeu0029","Dingo Disc","2 — 6","25","5+"],["jeu0030","Dixit","3 — 8","30","8+"],["jeu0031","Dobble","2 — 8","30","6+"],["jeu0032","Dobble Teams","2 — 8","30","6+"],["jeu0033","Escape Box - Minecraft","3 — 6","30 — 60","7+"],["jeu0034","First Martians","1 — 4","60 — 90","10+"],["jeu0035","Fortissimo!","2 — 4","30","6+"],["jeu0036","Gang Of Four","3 — 4","30","8+"],["jeu0037","Hanabi","2 — 5","30","8+"],["jeu0038","Harmonies","1 — 4","30","10+"],["jeu0039","Jarnac","Duo","40","7+"],["jeu0040","Jeu De Dominos Train Mexicain","2 — 8","30 — 45","6+"],["jeu0041","Jeu de l'oie des formes et couleurs","2 — 4","10","3+"],["jeu0042","Jeu du Toc à 6 joueurs","2 — 6","20 — 50","8+"],["jeu0043","Jungle Cache-Cache","Solo","15","5+"],["jeu0044","Kingdomino","2 — 4","15","8+"],["jeu0045","Kippit","Duo","30","5+"],["jeu0046","Kluster","1 — 4","15","14+"],["jeu0047","Kronologic - Cuzco 1450","1 — 4","30","10+"],["jeu0048","L'Âge de pierre","2 — 4","60 — 120","10+"],["jeu0049","La planche des pirates","2 — 4","15","5+"],["jeu0050","Le jeu du Tock","2 — 4","40","7+"],["jeu0051","Le Monstre des Couleurs","2 — 5","20","3+"],["jeu0052","Le Roi des Nains","3 — 5","40","10+"],["jeu0053","Le Trésor des Lutins","2 — 4","20","4+"],["jeu0054","Le Verger","2 — 8","15","3+"],["jeu0055","Le voleur de carottes","1 — 6","5","4+"],["jeu0056","Les Aventuriers du Rail","2 — 5","40","8+"],["jeu0057","Les Cinq Rois","1 — 7","30 — 45","8+"],["jeu0058","Les Loups-Garous de Thiercelieux","8 — 18","30","8+"],["jeu0059","Level 8","2 — 6","30 — 60","8+"],["jeu0060","Maman et Ses Petits","1 — 2","10","2+"],["jeu0061","Memory - Parlant des animaux","2 — 5","10","3+"],["jeu0062","Memory - Petit Ours Brun","2 — 4","10 — 30","3+"],["jeu0063","Memory - Petits Animaux","2 — 5","10","3+"],["jeu0064","Mini Family","2 — 4","10","4+"],["jeu0065","MiniMatch","2 — 5","10","3+"],["jeu0066","Mirogolo","4 — 12","45","9+"],["jeu0067","Mistigri","2 — 4","10","3+"],["jeu0068","Mixamatou","2 — 4","10","5+"],["jeu0069","Mon premier Carcassonne","2 — 4","10","4+"],["jeu0070","Mot pour Mot","2 — 16","20","8+"],["jeu0071","Nekojima","1 — 5","15","7+"],["jeu0072","Ni Hao Kai-Lan","2 — 4","10","3+"],["jeu0073","Papayoo","3 — 8","30 — 60","7+"],["jeu0074","Patchwork","Duo","30","8+"],["jeu0075","Pouic Pouic la Souris","2 — 4","15","3+"],["jeu0076","Présages","4 — 6","20 — 30","10+"],["jeu0077","Puissance 4","Duo","15 — 30","6+"],["jeu0078","Puzzle - Vachemenbien","Solo","10 — 20","1+"],["jeu0079","Puzzle Oui-Oui Jeu entre amis","Solo","15","3+"],["jeu0080","Quarto","Duo","15","8+"],["jeu0081","Qwirkle","2 — 4","30 — 45","6+"],["jeu0082","Rami Junior","2 — 6","20","6+"],["jeu0083","RapidCroco","2 — 5","15","4+"],["jeu0084","Rummikub Chiffres","2 — 4","45","10+"],["jeu0085","Rummikub Lettres","2 — 4","45","15+"],["jeu0086","Savannah Park","1 — 4","20 — 40","8+"],["jeu0087","Scrabble","2 — 4","60 — 90","10+"],["jeu0088","Shut The Books","3 — 4","40","7+"],["jeu0089","Similo - Contes","2 — 8","10","7+"],["jeu0090","Skip-Bo","2 — 6","30","7+"],["jeu0091","Skull King","2 — 8","30","8+"],["jeu0092","Skyjo","2 — 8","15 — 45","8+"],["jeu0093","Speech Contes de fée","1 — 8","15","6+"],["jeu0094","Splendor Duel","Duo","30","10+"],["jeu0095","Splito","3 — 8","15","8+"],["jeu0096","Super Mega Lucky Box","1 — 6","20","8+"],["jeu0097","Tarot","3 — 5","20","10+"],["jeu0098","Terristories","2 — 4","40","12+"],["jeu0099","The BoardGameGeek Game","3 — 6","60","8+"],["jeu0100","Time's Up !","4+","60","12+"],["jeu0101","Trio","3 — 6","15","7+"],["jeu0102","Triominos","2 — 4","30","6+"],["jeu0103","Triominos Classic","2 — 4","20","6+"],["jeu0104","Triominos Excel","2 — 6","30","6+"],["jeu0105","Triominos Junior","1 — 4","20","5+"],["jeu0106","Twin It!","2 — 6","15","6+"],["jeu0107","Voyage en France","2 — 6","45","8+"],["jeu0108","Wiz-War","2 — 4","30 — 60","14+"],["jeu0109","Zooloretto","2 — 5","45","8+"]
    ];

    let gamesUrls = {};
    let isAdminLoggedIn = sessionStorage.getItem('adminLoggedIn') === 'true';

    async function loadGamesUrls() {
        try {
            const { data } = await sb.from('regles').select('game_id, url');
            if (data) { data.forEach(r => { gamesUrls[r.game_id] = r.url; }); }
        } catch(e) {}
    }

    async function loadCustomGames() {
        try {
            const { data } = await sb.from('jeux_custom').select('*');
            if (data && data.length > 0) {
                data.forEach(g => {
                    if (!JEUX_BASE.find(j => j[0] === g.game_id)) {
                        JEUX_BASE.push([g.game_id, g.nom, g.joueurs, g.dures, g.age]);
                        if (g.url) gamesUrls[g.game_id] = g.url;
                    }
                });
            }
        } catch(e) {}
        JEUX_BASE.sort((a, b) => {
            const normalize = s => s.toLowerCase()
                .replace(/^(le |la |les |l'|l’)/i, '')
                .normalize("NFD").replace(/[̀-ͯ]/g, "");
            return normalize(a[1]).localeCompare(normalize(b[1]));
        });
    }

    async function saveGameUrl(gameId, url) {
        try {
            await sb.from('regles').upsert([{ game_id: gameId, url: url }], { onConflict: 'game_id' });
        } catch(e) {}
    }
    let adminPasswordHash = localStorage.getItem('adminHash');
    let isFirstAdminUse = !adminPasswordHash;
    let currentActivityType = null;

    const types = [
        { id: 'ballade', nom: 'Balade', icone: '🚶', couleur: '#4caf50' },
        { id: 'cinema', nom: 'Cinéma', icone: '🎬', couleur: '#2196f3' },
        { id: 'theatre', nom: 'Théâtre', icone: '🎭', couleur: '#9c27b0' },
        { id: 'resto', nom: 'Resto', icone: '🍽️', couleur: '#ff9800' },
        { id: 'visite', nom: 'Visite', icone: '🏛️', couleur: '#00bcd4' },
        { id: 'jeu', nom: 'Jeu', icone: '🎲', couleur: '#e91e63' },
        { id: 'surprise', nom: 'Et pourquoi pas ça ?', icone: '💡', couleur: '#795548' }
    ];

    const titles = {
        ballade: '🚶 Balade', cinema: '🎬 Cinéma', theatre: '🎭 Théâtre',
        resto: '🍽️ Resto', visite: '🏛️ Visite', jeu: '🎲 Jeu',
        surprise: '💡 Et pourquoi pas ça ?'
    };

    const typeCouleurs = {
        ballade: '#4caf50', cinema: '#2196f3', theatre: '#9c27b0',
        resto: '#ff9800', visite: '#00bcd4', jeu: '#e91e63', surprise: '#795548'
    };

    function escapeHtml(str) {
        if (!str) return "";
        return str.replace(/[&<>]/g, m => m === "&" ? "&amp;" : m === "<" ? "&lt;" : "&gt;");
    }

    function showMessage(containerId, msg, isError = true) {
        const div = document.getElementById(containerId);
        if (!div) return;
        div.innerHTML = `<div class="${isError ? 'error' : 'success'}">${msg}</div>`;
        setTimeout(() => div.innerHTML = '', 3500);
    }

    async function incrementVisits() {
        try {
            const { data } = await sb.from('visites').select('count').eq('id', 1).single();
            if (data) {
                const newCount = (data.count || 0) + 1;
                await sb.from('visites').update({ count: newCount }).eq('id', 1);
                document.getElementById('visitCount').textContent = newCount.toLocaleString('fr-FR');
            } else {
                await sb.from('visites').insert([{ id: 1, count: 1 }]);
                document.getElementById('visitCount').textContent = '1';
            }
        } catch (err) {
            document.getElementById('visitCount').textContent = '—';
        }
    }

    async function deleteExpiredEvents() {
        try {
            const now = new Date();
            const today = new Date(now.getFullYear(), now.getMonth(), now.getDate());
            const { data } = await sb.from('evenements').select('id, date_heure');
            if (!data) return;
            for (const ev of data) {
                const evDate = new Date(ev.date_heure);
                const evDay = new Date(evDate.getFullYear(), evDate.getMonth(), evDate.getDate());
                if (evDay < today) {
                    await sb.from('evenements').delete().eq('id', ev.id);
                }
            }
        } catch (err) { console.error('Erreur suppression auto:', err); }
    }

    async function fetchEvents() {
        try {
            const { data, error } = await sb.from('evenements').select('*').order('date_heure', { ascending: true });
            if (error) throw error;
            return data || [];
        } catch (err) { console.error("Erreur chargement:", err); return []; }
    }

    async function addEvent(eventData) {
        try {
            const { error } = await sb.from('evenements').insert([eventData]);
            if (error) throw error;
            return true;
        } catch (err) { console.error("Erreur création:", err); return false; }
    }

    async function updateEvent(eventId, updates) {
        try {
            const { error } = await sb.from('evenements').update(updates).eq('id', eventId);
            if (error) throw error;
            return true;
        } catch (err) { return false; }
    }

    async function deleteEvent(eventId) {
        if (!confirm("Supprimer cette sortie ?")) return false;
        try {
            const { error } = await sb.from('evenements').delete().eq('id', eventId);
            if (error) throw error;
            return true;
        } catch (err) { return false; }
    }

    async function initHomeButtons() {
        const container = document.getElementById('buttonsContainer');
        container.innerHTML = '';
        const events = await fetchEvents();

        for (const type of types) {
            const count = events.filter(e => e.type === type.id).length;
            const btn = document.createElement('button');
            btn.className = 'activity-btn';
            btn.style.backgroundColor = type.couleur;
            btn.innerHTML = `
                <div class="btn-icon">${type.icone}</div>
                <div class="btn-name">${type.nom}</div>
                ${count > 0 ? `<div class="btn-badge">${count}</div>` : ''}
            `;
            btn.onclick = () => showActivity(type.id);
            container.appendChild(btn);
        }

        const upcoming = events.slice(0, 5);
        const section = document.getElementById('upcomingSection');
        if (upcoming.length === 0) { section.innerHTML = ''; return; }

        section.innerHTML = `<div class="upcoming-title">📅 Prochaines sorties</div>`;
        for (const ev of upcoming) {
            let totalPersonnes = 0;
            if (ev.inscrits) {
                const participants = ev.inscrits.split(',').filter(s => s.trim());
                for (const p of participants) {
                    const parts = p.split(':');
                    const nb = parts.length > 1 ? parseInt(parts[1]) || 1 : 1;
                    totalPersonnes += nb;
                }
            }
            const couleur = typeCouleurs[ev.type] || '#888';
            const card = document.createElement('div');
            card.className = 'event-card-home';
            card.onclick = () => showActivity(ev.type);
            card.innerHTML = `
                <div>
                    <span class="type-tag" style="background:${couleur}">${titles[ev.type] || ev.type}</span>
                    <b>${escapeHtml(ev.titre)}</b>
                </div>
                <div style="text-align:right; color:#666; font-size:0.9rem;">
                    📅 ${new Date(ev.date_heure).toLocaleDateString('fr-FR', {day:'numeric', month:'short', hour:'2-digit', minute:'2-digit'})}<br>
                    👥 ${totalPersonnes}${ev.places_max > 0 ? `/${ev.places_max}` : ''}
                </div>
            `;
            section.appendChild(card);
        }
    }

    function extraireMaxPlaces(joueursStr) {
        if (!joueursStr) return null;
        const match = joueursStr.match(/(\d+)\s*—\s*(\d+)/);
        if (match) return parseInt(match[2]);
        if (joueursStr.toLowerCase().includes('duo')) return 2;
        if (joueursStr.toLowerCase().includes('solo')) return 1;
        return null;
    }

    async function renderEvents() {
        const container = document.getElementById("eventsList");
        if (!container) return;
        container.innerHTML = "<p style='text-align:center;color:#666;'>⏳ Chargement...</p>";
        let events = await fetchEvents();
        events = events.filter(e => e.type === currentActivityType);
        
        if (events.length === 0) {
            container.innerHTML = "<p style='text-align:center;color:#666;'>✨ Aucune sortie pour le moment.</p>";
            return;
        }
        container.innerHTML = "";
        
        const now = new Date();
        for (let ev of events) {
            const inscritsArr = ev.inscrits ? ev.inscrits.split(",").filter(s => s.trim()) : [];
            let participantsList = [];
            let totalPersonnes = 0;
            for (const p of inscritsArr) {
                const parts = p.split(':');
                const nom = parts[0];
                const nb = parts.length > 1 ? parseInt(parts[1]) || 1 : 1;
                participantsList.push({ nom, nb });
                totalPersonnes += nb;
            }
            
            let detailsHtml = '';
            if (ev.details) {
                try {
                    const d = JSON.parse(ev.details);
                    if (d.lieu) detailsHtml += `<div>📍 ${escapeHtml(d.lieu)}</div>`;
                    if (d.film) detailsHtml += `<div>🎞️ Film : ${escapeHtml(d.film)}</div>`;
                    if (d.piece) detailsHtml += `<div>🎭 Pièce : ${escapeHtml(d.piece)}</div>`;
                    if (d.gameTitle) {
                        detailsHtml += `<div>🎲 Jeu : ${escapeHtml(d.gameTitle)}</div>`;
                        if (d.rulesLink && d.rulesLink.trim()) detailsHtml += `<div>📖 <a href="${escapeHtml(d.rulesLink)}" target="_blank">Voir la règle</a></div>`;
                    }
                    if (d.description) detailsHtml += `<div>💬 ${escapeHtml(d.description)}</div>`;
                    if (d.createdBy) detailsHtml += `<div>👤 Proposé par : ${escapeHtml(d.createdBy)}</div>`;
                    if (d.infos) detailsHtml += `<div>📝 ${escapeHtml(d.infos)}</div>`;
                } catch(e) { detailsHtml = `<div>${escapeHtml(ev.details)}</div>`; }
            }
            
            const estTermine = new Date(ev.date_heure) < now;
            const aFaitRetour = ev.nb_presents !== null && ev.nb_presents !== undefined;
            
            let feedbackHtml = '';
            if (estTermine && !aFaitRetour) {
                const monPseudo = sessionStorage.getItem('monPseudo');
                const details = ev.details ? JSON.parse(ev.details) : {};
                const createur = details.createdBy;
                if (monPseudo && createur && monPseudo === createur) {
                    feedbackHtml = `
                        <div class="feedback-area" data-event-id="${ev.id}">
                            <b>📝 Ton avis sur cette sortie :</b>
                            <div>Vous étiez combien ? <input type="number" id="nbPresents_${ev.id}" placeholder="Nombre de participants" style="width:100px; display:inline-block;"></div>
                            <div>Ambiance :</div>
                            <div class="ambiance-buttons">
                                <button class="ambiance-btn" data-ambiance="vert">🟢</button>
                                <button class="ambiance-btn" data-ambiance="orange">🟠</button>
                                <button class="ambiance-btn" data-ambiance="rouge">🔴</button>
                            </div>
                            <button class="submit-feedback" data-id="${ev.id}">✅ Envoyer mon retour</button>
                        </div>
                    `;
                }
            }
            
            const div = document.createElement("div");
            div.className = "event-card";
            div.innerHTML = `
                <b>📌 ${escapeHtml(ev.titre)}</b><br>
                📅 ${new Date(ev.date_heure).toLocaleString()}<br>
                ${detailsHtml}
                👥 ${totalPersonnes}${ev.places_max > 0 ? `/${ev.places_max}` : ''} places<br>
                <div id="participantsList_${ev.id}">
                    ${participantsList.map(p => `
                        <div class="participant-line" data-nom="${escapeHtml(p.nom)}">
                            <span>${escapeHtml(p.nom)} (${p.nb} personne${p.nb > 1 ? 's' : ''})</span>
                            <div class="participant-actions">
                                <button class="edit-participant" data-nom="${escapeHtml(p.nom)}" data-ev-id="${ev.id}">✏️</button>
                                <button class="remove-participant" data-nom="${escapeHtml(p.nom)}" data-ev-id="${ev.id}">❌</button>
                            </div>
                        </div>
                    `).join('')}
                </div>
                ${!estTermine ? `<button class="joinGameBtn" data-id="${ev.id}">👍 Je participe</button>` : ''}
                ${isAdminLoggedIn ? `<button class="deleteBtn" data-id="${ev.id}" style="background:#d32f2f;">🗑️ Supprimer</button>` : ''}
                ${feedbackHtml}
            `;
            container.appendChild(div);
            
            if (!estTermine) {
                div.querySelector(".joinGameBtn")?.addEventListener("click", async () => {
                    let pseudo = sessionStorage.getItem('monPseudo');
                    if (!pseudo) {
                        pseudo = prompt("Ton prénom :");
                        if (!pseudo) return;
                        sessionStorage.setItem('monPseudo', pseudo);
                    }
                    let nbPersonnes = prompt("Vous serez combien ? (nombre de personnes)", "1");
                    if (!nbPersonnes) return;
                    nbPersonnes = parseInt(nbPersonnes);
                    if (isNaN(nbPersonnes) || nbPersonnes < 1) nbPersonnes = 1;
                    
                    const eventsList = await fetchEvents();
                    const currentEv = eventsList.find(e => e.id === ev.id);
                    let inscrits = currentEv.inscrits ? currentEv.inscrits.split(",").filter(s => s.trim()) : [];
                    let totalActuel = 0;
                    const participantsMap = {};
                    for (const p of inscrits) {
                        const parts = p.split(':');
                        const nom = parts[0];
                        const nb = parts.length > 1 ? parseInt(parts[1]) || 1 : 1;
                        participantsMap[nom] = nb;
                        totalActuel += nb;
                    }
                    if (currentEv.places_max > 0 && totalActuel + nbPersonnes > currentEv.places_max) {
                        alert("Il n'y a plus assez de places !");
                        return;
                    }
                    if (participantsMap[pseudo]) {
                        alert("Tu es déjà inscrit !");
                        return;
                    }
                    participantsMap[pseudo] = nbPersonnes;
                    const newInscrits = Object.entries(participantsMap).map(([nom, nb]) => `${nom}:${nb}`).join(",");
                    await updateEvent(ev.id, { inscrits: newInscrits });
                    showMessage("message", "✅ Inscription ajoutée !", false);
                    renderEvents();
                });
            }
            
            div.querySelectorAll(".edit-participant").forEach(btn => {
                btn.addEventListener("click", async () => {
                    const nom = btn.getAttribute("data-nom");
                    const monPseudo = sessionStorage.getItem('monPseudo');
                    if (monPseudo !== nom) {
                        alert("Tu ne peux modifier que tes propres informations.");
                        return;
                    }
                    const newNb = prompt(`Nouveau nombre de personnes pour ${nom} ?`, "");
                    if (!newNb) return;
                    const nbInt = parseInt(newNb);
                    if (isNaN(nbInt) || nbInt < 1) return;
                    const eventsList = await fetchEvents();
                    const currentEv = eventsList.find(e => e.id === ev.id);
                    let inscrits = currentEv.inscrits ? currentEv.inscrits.split(",").filter(s => s.trim()) : [];
                    const participantsMap = {};
                    for (const p of inscrits) {
                        const parts = p.split(':');
                        const pNom = parts[0];
                        const pNb = parts.length > 1 ? parseInt(parts[1]) || 1 : 1;
                        participantsMap[pNom] = pNb;
                    }
                    let totalSansLui = 0;
                    for (const [pNom, pNb] of Object.entries(participantsMap)) {
                        if (pNom !== nom) totalSansLui += pNb;
                    }
                    if (currentEv.places_max > 0 && totalSansLui + nbInt > currentEv.places_max) {
                        alert("Dépassement du nombre de places disponibles !");
                        return;
                    }
                    participantsMap[nom] = nbInt;
                    const newInscrits = Object.entries(participantsMap).map(([pNom, pNb]) => `${pNom}:${pNb}`).join(",");
                    await updateEvent(ev.id, { inscrits: newInscrits });
                    showMessage("message", "✅ Nombre modifié !", false);
                    renderEvents();
                });
            });
            
            div.querySelectorAll(".remove-participant").forEach(btn => {
                btn.addEventListener("click", async () => {
                    const nom = btn.getAttribute("data-nom");
                    const monPseudo = sessionStorage.getItem('monPseudo');
                    if (monPseudo !== nom) {
                        alert("Tu ne peux retirer que toi-même.");
                        return;
                    }
                    if (!confirm(`Retirer ${nom} ?`)) return;
                    const eventsList = await fetchEvents();
                    const currentEv = eventsList.find(e => e.id === ev.id);
                    let inscrits = currentEv.inscrits ? currentEv.inscrits.split(",").filter(s => s.trim()) : [];
                    const newInscrits = inscrits.filter(p => !p.startsWith(nom + ":"));
                    await updateEvent(ev.id, { inscrits: newInscrits.join(",") });
                    showMessage("message", "❌ Participant retiré.", false);
                    renderEvents();
                });
            });
            
            div.querySelectorAll(".submit-feedback").forEach(btn => {
                btn.addEventListener("click", async () => {
                    const eventId = btn.getAttribute("data-id");
                    const nbPresents = document.getElementById(`nbPresents_${eventId}`)?.value;
                    const ambianceBtn = btn.closest('.feedback-area')?.querySelector('.ambiance-btn.selected');
                    const ambiance = ambianceBtn?.getAttribute('data-ambiance');
                    if (!nbPresents || !ambiance) {
                        alert("Merci de renseigner le nombre de participants et l'ambiance.");
                        return;
                    }
                    await updateEvent(eventId, { nb_presents: parseInt(nbPresents), ambiance: ambiance });
                    showMessage("message", "Merci pour ton retour !", false);
                    renderEvents();
                });
            });
            
            div.querySelectorAll(".ambiance-btn").forEach(btn => {
                btn.addEventListener("click", () => {
                    const parent = btn.closest('.feedback-area');
                    parent.querySelectorAll('.ambiance-btn').forEach(b => b.classList.remove('selected'));
                    btn.classList.add('selected');
                });
            });
        }

        if (isAdminLoggedIn) {
            document.querySelectorAll(".deleteBtn").forEach(btn => {
                btn.onclick = async () => {
                    const id = btn.getAttribute("data-id");
                    if (await deleteEvent(id)) {
                        showMessage("message", "🗑️ Supprimée.", false);
                        renderEvents();
                    }
                };
            });
        }
    }

    function generateFields() {
        const container = document.getElementById('dynamicFields');
        container.innerHTML = '';
        if (currentActivityType === 'jeu') {
            let selectOptions = '<option value="">-- Sélectionne dans la liste --</option>';
            for (let g of JEUX_BASE) {
                selectOptions += `<option value="${escapeHtml(g[0])}">${escapeHtml(g[1])} (${escapeHtml(g[2])} joueurs · ${escapeHtml(g[4])})</option>`;
            }
            selectOptions += '<option value="__cartes__">🃏 Jeu de cartes (à préciser)</option>';

            container.innerHTML = `
                <label>📋 Ou choisis dans la liste</label>
                <select id="gameSelect">${selectOptions}</select>
                <div id="customGameDiv" style="display:none;" class="cards-game-area">
                    <strong>🃏 JEUX DE CARTES</strong><br>
                    <label>✏️ Précise le jeu de cartes *</label>
                    <input type="text" id="customGameName" placeholder="Ex: Belote, Tarot, Rami, Coinche...">
                </div>
                <div id="gameSelectedDisplay" style="display:none;"></div>
                <input type="hidden" id="gameSelectedId">
                <input type="hidden" id="gameSelectedName">
                <label>📍 Lieu (optionnel)</label>
                <input type="text" id="lieu">
                <label>📝 Infos complémentaires</label>
                <textarea id="details" rows="2"></textarea>
            `;

            const gameSelect = document.getElementById('gameSelect');
            const customDiv = document.getElementById('customGameDiv');
            const maxParticipantsInput = document.getElementById('maxParticipants');
            
            gameSelect.addEventListener('change', () => {
                const selectedId = gameSelect.value;
                if (selectedId === '__cartes__') {
                    customDiv.style.display = 'block';
                    if (maxParticipantsInput) maxParticipantsInput.disabled = false;
                } else if (selectedId) {
                    customDiv.style.display = 'none';
                    const game = JEUX_BASE.find(g => g[0] === selectedId);
                    if (game) {
                        const maxPlaces = extraireMaxPlaces(game[2]);
                        if (maxPlaces && maxParticipantsInput) {
                            maxParticipantsInput.value = maxPlaces;
                            maxParticipantsInput.disabled = false;
                        } else if (maxParticipantsInput) {
                            maxParticipantsInput.disabled = false;
                        }
                    }
                } else {
                    customDiv.style.display = 'none';
                }
            });
        } else {
            container.innerHTML = `<label>📍 Lieu *</label><input type="text" id="lieu" required><label>📝 Infos complémentaires</label><textarea id="details" rows="2"></textarea>`;
        }
    }

    async function createActivity() {
        const datetime = document.getElementById("datetime").value;
        let max = parseInt(document.getElementById("maxParticipants").value);
        const isUnlimited = document.getElementById("unlimitedCheckbox").checked;
        const creatorName = document.getElementById("creatorName").value.trim();
        if (!datetime) { alert("Choisis une date et heure"); return; }
        if (!creatorName) { alert("Entre ton nom"); return; }
        if (isUnlimited) max = -1;

        let title = "";
        let detailsObj = { createdBy: creatorName };

        if (currentActivityType === 'jeu') {
            const gameSelect = document.getElementById('gameSelect');
            const selectedId = gameSelect?.value;
            let gameTitle = "", rulesLink = "";
            if (selectedId === '__cartes__') {
                const customGame = document.getElementById("customGameName")?.value.trim();
                if (!customGame) { alert("Précise le jeu de cartes"); return; }
                gameTitle = `Jeu de cartes : ${customGame}`;
            } else if (selectedId) {
                const game = JEUX_BASE.find(g => g[0] === selectedId);
                if (game) {
                    gameTitle = game[1];
                    if (gamesUrls[selectedId]) rulesLink = gamesUrls[selectedId];
                }
            } else { alert("Choisis un jeu dans la liste"); return; }
            title = `Jeu : ${gameTitle}`;
            detailsObj.gameTitle = gameTitle;
            if (rulesLink) detailsObj.rulesLink = rulesLink;
            const lieu = document.getElementById("lieu")?.value.trim() || "";
            if (lieu) detailsObj.lieu = lieu;
        } else {
            const lieu = document.getElementById("lieu")?.value.trim();
            if (!lieu) { alert("Indique le lieu"); return; }
            title = `${titles[currentActivityType]} : ${lieu}`;
            detailsObj.lieu = lieu;
        }
        
        const infos = document.getElementById("details")?.value.trim() || "";
        if (infos) detailsObj.infos = infos;

        const newEvent = {
            id: Date.now().toString(),
            type: currentActivityType,
            titre: title,
            date_heure: datetime,
            places_max: max,
            inscrits: "",
            details: JSON.stringify(detailsObj),
            nb_presents: null,
            ambiance: null
        };

        showMessage("message", "⏳ Création en cours...", false);
        document.getElementById("saveBtn").disabled = true;
        const success = await addEvent(newEvent);
        document.getElementById("saveBtn").disabled = false;
        if (success) {
            showMessage("message", "🎉 Table créée !", false);
            document.getElementById("form").style.display = "none";
            document.getElementById("datetime").value = "";
            document.getElementById("maxParticipants").value = "10";
            document.getElementById("unlimitedCheckbox").checked = false;
            document.getElementById("creatorName").value = "";
            renderEvents();
        } else {
            showMessage("message", "❌ Erreur création");
        }
    }

    function showHome() {
        document.getElementById("homePage").classList.add("active");
        document.getElementById("activityPage").classList.remove("active");
        document.getElementById("adminPage").classList.remove("active");
        currentActivityType = null;
        initHomeButtons();
    }

    function showActivity(typeId) {
        currentActivityType = typeId;
        document.getElementById("homePage").classList.remove("active");
        document.getElementById("activityPage").classList.add("active");
        document.getElementById("adminPage").classList.remove("active");
        document.getElementById("pageTitle").innerHTML = titles[typeId];
        const btnLabel = typeId === 'jeu' ? '🎲 Proposer une partie' : '✨ Proposer une sortie';
        document.getElementById("showFormBtn").innerHTML = btnLabel;
        document.getElementById("form").style.display = "none";
        document.getElementById("message").innerHTML = "";
        renderEvents();
    }

    function initAdmin() {
        const adminDiv = document.getElementById("adminArea");
        if (isFirstAdminUse || !adminPasswordHash) {
            adminDiv.innerHTML = `<div class="info">🔐 Première utilisation - Crée ton mot de passe admin</div>
                <input type="password" id="newAdminPwd" placeholder="Nouveau mot de passe"><br>
                <input type="password" id="confirmAdminPwd" placeholder="Confirmer"><br>
                <button id="setAdminPwdBtn">✅ Créer mot de passe</button>`;
            document.getElementById("setAdminPwdBtn")?.addEventListener("click", () => {
                const pwd1 = document.getElementById("newAdminPwd").value;
                const pwd2 = document.getElementById("confirmAdminPwd").value;
                if (!pwd1 || pwd1 !== pwd2) { alert("Non identiques !"); return; }
                localStorage.setItem('adminHash', hashPassword(pwd1));
                alert("Mot de passe créé !");
                adminPasswordHash = hashPassword(pwd1);
                isFirstAdminUse = false;
                initAdmin();
            });
            return;
        }
        if (!isAdminLoggedIn) {
            const pwd = prompt("🔐 Mot de passe admin :");
            if (!pwd || !verifyAdminPassword(pwd)) { alert("Accès refusé."); document.getElementById("backToHomeFromAdmin").click(); return; }
            sessionStorage.setItem('adminLoggedIn', 'true');
            isAdminLoggedIn = true;
        }
        let html = `<div class="info">✏️ Admin connecté</div>`;
        html += `<h3>📊 Rapport d'activités</h3>`;
        html += `<div><label>📅 Du</label><input type="date" id="rapportDu"><label>📅 Au</label><input type="date" id="rapportAu"><button id="genRapportBtn">📊 Générer</button></div><div id="rapportResult"></div>`;
        adminDiv.innerHTML = html;
        
        document.getElementById('genRapportBtn')?.addEventListener('click', async () => {
            const du = document.getElementById('rapportDu').value;
            const au = document.getElementById('rapportAu').value;
            if (!du || !au) { alert("Choisis une période"); return; }
            const events = await fetchEvents();
            const debut = new Date(du);
            const fin = new Date(au); fin.setHours(23,59,59);
            const filtered = events.filter(e => new Date(e.date_heure) >= debut && new Date(e.date_heure) <= fin);
            if (filtered.length === 0) {
                document.getElementById('rapportResult').innerHTML = '<div class="info">Aucune activité.</div>';
                return;
            }
            let htmlR = '<div><table style="width:100%;border-collapse:collapse;"><tr><th>Activité</th><th>Date</th><th>Inscrits</th><th>Présents</th><th>Taux</th><th>Ambiance</th></tr>';
            for (const ev of filtered) {
                let totalInscrits = 0;
                if (ev.inscrits) {
                    const parts = ev.inscrits.split(',');
                    for (const p of parts) {
                        const nb = p.split(':').length > 1 ? parseInt(p.split(':')[1]) || 1 : 1;
                        totalInscrits += nb;
                    }
                }
                const presents = ev.nb_presents || '-';
                const taux = presents !== '-' && totalInscrits > 0 ? Math.round((presents / totalInscrits) * 100) + '%' : '-';
                const ambianceMap = { vert: '🟢', orange: '🟠', rouge: '🔴' };
                const ambianceIcon = ambianceMap[ev.ambiance] || '-';
                htmlR += `<tr><td>${ev.titre}</td><td>${new Date(ev.date_heure).toLocaleDateString()}</td><td>${totalInscrits}</td><td>${presents}</td><td>${taux}</td><td>${ambianceIcon}</td></tr>`;
            }
            htmlR += '</table></div>';
            document.getElementById('rapportResult').innerHTML = htmlR;
        });
    }

    function hashPassword(pwd) { let hash = 0; for (let i = 0; i < pwd.length; i++) { hash = ((hash << 5) - hash) + pwd.charCodeAt(i); hash |= 0; } return hash.toString(); }
    function verifyAdminPassword(pwd) { const stored = localStorage.getItem('adminHash'); if (!stored) return false; return hashPassword(pwd) === stored; }
    function adminLogout() { sessionStorage.removeItem('adminLoggedIn'); isAdminLoggedIn = false; alert("🔓 Déconnecté."); showHome(); }
    function showAdmin() { document.getElementById("homePage").classList.remove("active"); document.getElementById("activityPage").classList.remove("active"); document.getElementById("adminPage").classList.add("active"); initAdmin(); }

    document.getElementById("backToHome").onclick = showHome;
    document.getElementById("backToHomeFromAdmin").onclick = showHome;
    document.getElementById("adminLink").onclick = (e) => { e.preventDefault(); showAdmin(); };
    document.getElementById("logoutAdminBtn").onclick = adminLogout;
    document.getElementById("showFormBtn").onclick = () => { generateFields(); document.getElementById("form").style.display = "block"; };
    document.getElementById("cancelBtn").onclick = () => { document.getElementById("form").style.display = "none"; };
    document.getElementById("saveBtn").onclick = createActivity;
    document.getElementById("refreshPageBtn").onclick = () => location.reload();
    document.getElementById("unlimitedCheckbox").onchange = (e) => {
        const maxInput = document.getElementById("maxParticipants");
        if (e.target.checked) {
            maxInput.disabled = true;
            maxInput.value = "";
        } else {
            maxInput.disabled = false;
            maxInput.value = "10";
        }
    };

    await loadGamesUrls();
    await loadCustomGames();
    await deleteExpiredEvents();
    await incrementVisits();
    await initHomeButtons();
</script>
</body>
</html>
