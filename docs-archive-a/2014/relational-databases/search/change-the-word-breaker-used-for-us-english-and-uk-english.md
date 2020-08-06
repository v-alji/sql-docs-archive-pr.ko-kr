---
title: 미국 영어 및 영국 영어에 사용되는 단어 분리기 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: 6b5d2177-db98-47f5-b32e-4b80a2f74ffe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3b759b90ec834dcb666f7862bfba3857f2fea0d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651616"
---
# <a name="change-the-word-breaker-used-for-us-english-and-uk-english"></a><span data-ttu-id="52107-102">미국 영어 및 영국 영어에 사용되는 단어 분리기 변경</span><span class="sxs-lookup"><span data-stu-id="52107-102">Change the Word Breaker Used for US English and UK English</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="52107-103">에서는 영어용 단어 분리기 및 형태소 분석기의 새 버전(버전 14.0.4999.1038)을 설치하여 이전 버전(버전 12.0.6828.0)의 해당 구성 요소를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-103">installs a new version (version 14.0.4999.1038) of the word breaker and stemmer for the English language, replacing the previous version of these components (version 12.0.6828.0).</span></span> <span data-ttu-id="52107-104">새 구성 요소의 변경된 동작에 대한 자세한 내용은 [전체 텍스트 검색의 동작 변경](full-text-search.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52107-104">For information about the changed behavior of the new components, see [Behavior Changes to Full-Text Search](full-text-search.md).</span></span> <span data-ttu-id="52107-105">이 항목에서는 이러한 새 버전의 구성 요소에서 이전 버전으로 전환하거나 이전 버전에서 다시 새 버전으로 전환하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-105">This topic describes how to switch from the new version of these components to the previous version, or to switch back from the previous version to the new version.</span></span> <span data-ttu-id="52107-106">클러스터 설치의 경우 이러한 변경은 모든 주 노드 및 패시브 노드에서 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-106">For cluster installations, these changes should be made on all the primary and passive nodes.</span></span>  
  
 <span data-ttu-id="52107-107">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 미국 영어(LCID 1033은)와 영국 영어(LCID 2057)에 대해 각기 다른 CLSID로 표시되는 서로 다른 단어 분리기가 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="52107-107">Previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] used different word breakers represented by different CLSIDs for US English (LCID 1033) and UK English (LCID 2057).</span></span> <span data-ttu-id="52107-108">이번 릴리스에서는 다음 표와 같이 두 LCID 모두 동일한 CLSID를 갖는 동일한 구성 요소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-108">In this release, both LCIDs use the same components with the same CLSIDs, as shown in the following table:</span></span>  
  
|<span data-ttu-id="52107-109">LCID</span><span class="sxs-lookup"><span data-stu-id="52107-109">LCID</span></span>|<span data-ttu-id="52107-110">이전 버전에서 설치된 단어 분리기</span><span class="sxs-lookup"><span data-stu-id="52107-110">Word breaker installed by previous versions</span></span><br /><br /> <span data-ttu-id="52107-111">버전 12.0.6828.0</span><span class="sxs-lookup"><span data-stu-id="52107-111">version 12.0.6828.0</span></span>|<span data-ttu-id="52107-112">이전 버전에서 설치된 형태소 분석기</span><span class="sxs-lookup"><span data-stu-id="52107-112">Stemmer installed by previous versions</span></span>|<span data-ttu-id="52107-113">이번 버전에서 설치되는 단어 분리기</span><span class="sxs-lookup"><span data-stu-id="52107-113">Word breaker installed by this version</span></span><br /><br /> <span data-ttu-id="52107-114">버전 14.0.4999.1038</span><span class="sxs-lookup"><span data-stu-id="52107-114">version 14.0.4999.1038</span></span>|<span data-ttu-id="52107-115">이번 버전에서 설치되는 형태소 분석기</span><span class="sxs-lookup"><span data-stu-id="52107-115">Stemmer installed by this version</span></span>|  
|----------|-------------------------------------------------------------------------|--------------------------------------------|-----------------------------------------------------------------------|---------------------------------------|  
|<span data-ttu-id="52107-116">1033</span><span class="sxs-lookup"><span data-stu-id="52107-116">1033</span></span><br /><span data-ttu-id="52107-117">(미국 영어)</span><span class="sxs-lookup"><span data-stu-id="52107-117">(US English)</span></span>|<span data-ttu-id="52107-118">188D6CC5-CB03-4C01-912E-47D21295D77E</span><span class="sxs-lookup"><span data-stu-id="52107-118">188D6CC5-CB03-4C01-912E-47D21295D77E</span></span>|<span data-ttu-id="52107-119">EEED4C20-7F1B-11CE-BE57-00AA0051FE20</span><span class="sxs-lookup"><span data-stu-id="52107-119">EEED4C20-7F1B-11CE-BE57-00AA0051FE20</span></span>|<span data-ttu-id="52107-120">9faed859-0b30-4434-ae65-412e14a16fb8</span><span class="sxs-lookup"><span data-stu-id="52107-120">9faed859-0b30-4434-ae65-412e14a16fb8</span></span>|<span data-ttu-id="52107-121">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span><span class="sxs-lookup"><span data-stu-id="52107-121">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span></span>|  
|<span data-ttu-id="52107-122">2057</span><span class="sxs-lookup"><span data-stu-id="52107-122">2057</span></span><br /><span data-ttu-id="52107-123">(영국 영어)</span><span class="sxs-lookup"><span data-stu-id="52107-123">(UK English)</span></span>|<span data-ttu-id="52107-124">173C97E2-AEBE-437C-9445-01B237ABF2F6</span><span class="sxs-lookup"><span data-stu-id="52107-124">173C97E2-AEBE-437C-9445-01B237ABF2F6</span></span>|<span data-ttu-id="52107-125">D99F7670-7F1A-11CE-BE57-00AA0051FE20</span><span class="sxs-lookup"><span data-stu-id="52107-125">D99F7670-7F1A-11CE-BE57-00AA0051FE20</span></span>|<span data-ttu-id="52107-126">9faed859-0b30-4434-ae65-412e14a16fb8</span><span class="sxs-lookup"><span data-stu-id="52107-126">9faed859-0b30-4434-ae65-412e14a16fb8</span></span>|<span data-ttu-id="52107-127">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span><span class="sxs-lookup"><span data-stu-id="52107-127">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span></span>|  
  
 <span data-ttu-id="52107-128">이 항목에서 설명하는 구성 요소는 `MSSQL\Binn` 인스턴스의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 폴더에 설치되는 DLL 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="52107-128">The components described in this topic are DLL files that are installed in the `MSSQL\Binn` folder for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="52107-129">전체 경로는 일반적으로 `C:\Program Files\Microsoft SQL Server\<instance>\MSSQL\Binn`입니다.</span><span class="sxs-lookup"><span data-stu-id="52107-129">The full path is typically `C:\Program Files\Microsoft SQL Server\<instance>\MSSQL\Binn`.</span></span>  
  
 <span data-ttu-id="52107-130">단어 분리기 및 형태소 분석기에 대한 자세한 내용은 [검색을 위해 단어 분리기와 형태소 분석기 구성 및 관리](configure-and-manage-word-breakers-and-stemmers-for-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52107-130">For more information about word breakers and stemmers, see [Configure and Manage Word Breakers and Stemmers for Search](configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  
## <a name="switching-from-the-current-english-word-breaker-to-the-previous-english-word-breakers"></a><span data-ttu-id="52107-131">현재 영어 단어 분리기를 이전 영어 단어 분리기로 전환</span><span class="sxs-lookup"><span data-stu-id="52107-131">Switching from the current English word breaker to the previous English word breakers</span></span>  
  
#### <a name="to-switch-from-the-current-version-of-the-us-english-word-breaker-to-the-previous-version"></a><span data-ttu-id="52107-132">현재 버전의 미국 영어 단어 분리기를 이전 버전으로 전환하려면</span><span class="sxs-lookup"><span data-stu-id="52107-132">To switch from the current version of the US English word breaker to the previous version</span></span>  
  
1.  <span data-ttu-id="52107-133">레지스트리에서 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID** 노드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-133">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="52107-134">다음 단계에 따라 LCID 1033의 이전 미국 영어 단어 분리기 및 형태소 분석기 인터페이스에 대한 COM ClassID의 새 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-134">Use the following steps to add new keyS for the COM ClassIDs for the previous US English word breaker and stemmer interfaces for LCID 1033:</span></span>  
  
    1.  <span data-ttu-id="52107-135">이전 단어 분리기의 **{188D6CC5-CB03-4C01-912E-47D21295D77E}** 값을 사용하여 새 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-135">Add a new key with the value **{188D6CC5-CB03-4C01-912E-47D21295D77E}** for the previous word breaker.</span></span>  
  
    2.  <span data-ttu-id="52107-136">해당 키 값의 (기본값) 데이터를 **langwrbk.dll**로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-136">Update the (Default) data of that key value to **langwrbk.dll**.</span></span>  
  
    3.  <span data-ttu-id="52107-137">이전 형태소 분석기의 **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** 값을 사용하여 새 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-137">Add a new key with the value **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** for the previous stemmer.</span></span>  
  
    4.  <span data-ttu-id="52107-138">해당 키 값의 (기본값) 데이터를 **infosoft.dll**로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-138">Update the (Default) data of that key value to **infosoft.dll**.</span></span>  
  
3.  <span data-ttu-id="52107-139">레지스트리에서 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\enu** 노드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-139">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\enu**.</span></span>  
  
4.  <span data-ttu-id="52107-140">**WBreakerClass** 키 값을 **{188D6CC5-CB03-4C01-912E-47D21295D77E}** 로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-140">Update the **WBreakerClass** key value to **{188D6CC5-CB03-4C01-912E-47D21295D77E}**.</span></span>  
  
5.  <span data-ttu-id="52107-141">**StemmerClass** 키 값을 **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** 으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-141">Update the **StemmerClass** key value to **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}**.</span></span>  
  
6.  <span data-ttu-id="52107-142">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-142">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="to-switch-from-the-current-version-of-the-uk-english-word-breaker-to-the-previous-version"></a><span data-ttu-id="52107-143">현재 버전의 영국 영어 단어 분리기에서 이전 버전으로 전환하려면</span><span class="sxs-lookup"><span data-stu-id="52107-143">To switch from the current version of the UK English word breaker to the previous version</span></span>  
  
1.  <span data-ttu-id="52107-144">레지스트리에서 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID** 노드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-144">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="52107-145">다음 단계에 따라 LCID 2057의 이전 영국 영어 단어 분리기 및 형태소 분석기 인터페이스에 대한 COM ClassID의 새 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-145">Use the following steps to add a new key for the COM ClassIDs for the previous UK English word breaker and stemmer interfaces for LCID 2057:</span></span>  
  
    1.  <span data-ttu-id="52107-146">이전 단어 분리기의 **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** 값을 사용하여 새 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-146">Add a new key with the value **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** for the previous word breaker.</span></span>  
  
    2.  <span data-ttu-id="52107-147">해당 키 값의 (기본값) 데이터를 **langwrbk.dll**로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-147">Update the (Default) data of that key value to **langwrbk.dll**.</span></span>  
  
    3.  <span data-ttu-id="52107-148">이전 형태소 분석기의 **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** 값을 사용하여 새 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-148">Add a new key with the value **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** for the previous stemmer.</span></span>  
  
    4.  <span data-ttu-id="52107-149">해당 키 값의 (기본값) 데이터를 **infosoft.dll**로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-149">Update the (Default) data of that key value to **infosoft.dll**.</span></span>  
  
3.  <span data-ttu-id="52107-150">레지스트리에서 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng** 노드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-150">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.</span></span>  
  
4.  <span data-ttu-id="52107-151">**WBreakerClass** 키 값을 **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** 으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-151">Update the **WBreakerClass** key value to **{173C97E2-AEBE-437C-9445-01B237ABF2F6}**.</span></span>  
  
5.  <span data-ttu-id="52107-152">**StemmerClass** 키 값을 **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** 으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-152">Update the **StemmerClass** key value to **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}**.</span></span>  
  
6.  <span data-ttu-id="52107-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-153">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="switching-back-from-the-previous-english-word-breakers-to-the-current-english-word-breaker"></a><span data-ttu-id="52107-154">이전 영어 단어 분리기에서 다시 현재 영어 단어 분리기로 전환</span><span class="sxs-lookup"><span data-stu-id="52107-154">Switching back from the previous English word breakers to the current English word breaker</span></span>  
  
#### <a name="to-switch-back-from-the-previous-version-of-the-us-english-word-breaker-to-the-current-version"></a><span data-ttu-id="52107-155">이전 버전의 미국 영어 단어 분리기에서 현재 버전으로 전환하려면</span><span class="sxs-lookup"><span data-stu-id="52107-155">To switch back from the previous version of the US English word breaker to the current version</span></span>  
  
1.  <span data-ttu-id="52107-156">레지스트리에서 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID** 노드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-156">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="52107-157">다음 키가 없으면 다음 단계에 따라 LCID 1033의 현재 미국 영어 단어 분리기 및 형태소 분석기 인터페이스에 대한 COM ClassID의 새 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-157">If the following keys do not exist, then use the following steps to add a new key for the COM ClassIDs for the current US English word breaker and stemmer interfaces for LCID 1033:</span></span>  
  
    1.  <span data-ttu-id="52107-158">현재 단어 분리기의 **{9faed859-0b30-4434-ae65-412e14a16fb8}** 값을 사용하여 새 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-158">Add a new key with the value **{9faed859-0b30-4434-ae65-412e14a16fb8}** for the current word breaker.</span></span>  
  
    2.  <span data-ttu-id="52107-159">해당 키 값의 (기본값) 데이터를 **MsWb7.dll**로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-159">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
    3.  <span data-ttu-id="52107-160">현재 형태소 분석기의 **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** 값을 사용하여 새 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-160">Add a new key with the value **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** for the current stemmer.</span></span>  
  
    4.  <span data-ttu-id="52107-161">해당 키 값의 (기본값) 데이터를 **MsWb7.dll**로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-161">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
3.  <span data-ttu-id="52107-162">레지스트리에서 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng** 노드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-162">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.</span></span>  
  
4.  <span data-ttu-id="52107-163">**WBreakerClass** 키 값을 **{9faed859-0b30-4434-ae65-412e14a16fb8}** 로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-163">Update the **WBreakerClass** key value to **{9faed859-0b30-4434-ae65-412e14a16fb8}**.</span></span>  
  
5.  <span data-ttu-id="52107-164">**StemmerClass** 키 값을 **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** 로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-164">Update the **StemmerClass** key value to **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.</span></span>  
  
6.  <span data-ttu-id="52107-165">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-165">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="to-switch-back-from-the-previous-version-of-the-uk-english-word-breaker-to-the-current-version"></a><span data-ttu-id="52107-166">이전 버전의 영국 영어 단어 분리기에서 현재 버전으로 전환하려면</span><span class="sxs-lookup"><span data-stu-id="52107-166">To switch back from the previous version of the UK English word breaker to the current version</span></span>  
  
1.  <span data-ttu-id="52107-167">레지스트리에서 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID** 노드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-167">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="52107-168">다음 키가 없으면 다음 단계에 따라 LCID 2057의 현재 영국 영어 단어 분리기 및 형태소 분석기 인터페이스에 대한 COM ClassID의 새 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-168">If the following keys do not exist, then use the following steps to add a new key for the COM ClassIDs for the current UK English word breaker and stemmer interfaces for LCID 2057:</span></span>  
  
    1.  <span data-ttu-id="52107-169">현재 단어 분리기의 **{9faed859-0b30-4434-ae65-412e14a16fb8}** 값을 사용하여 새 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-169">Add a new key with the value **{9faed859-0b30-4434-ae65-412e14a16fb8}** for the current word breaker.</span></span>  
  
    2.  <span data-ttu-id="52107-170">해당 키 값의 (기본값) 데이터를 **MsWb7.dll**로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-170">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
    3.  <span data-ttu-id="52107-171">현재 형태소 분석기의 **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** 값을 사용하여 새 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-171">Add a new key with the value **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** for the current stemmer.</span></span>  
  
    4.  <span data-ttu-id="52107-172">해당 키 값의 (기본값) 데이터를 **MsWb7.dll**로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-172">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
3.  <span data-ttu-id="52107-173">레지스트리에서 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng** 노드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-173">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.</span></span>  
  
4.  <span data-ttu-id="52107-174">**WBreakerClass** 키 값을 **{9faed859-0b30-4434-ae65-412e14a16fb8}** 로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-174">Update the **WBreakerClass** key value to **{9faed859-0b30-4434-ae65-412e14a16fb8}**.</span></span>  
  
5.  <span data-ttu-id="52107-175">**StemmerClass** 키 값을 **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** 로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-175">Update the **StemmerClass** key value to **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.</span></span>  
  
6.  <span data-ttu-id="52107-176">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="52107-176">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52107-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52107-177">See Also</span></span>  
 <span data-ttu-id="52107-178">[검색에 사용된 단어 분리기를 이전 버전으로 되돌리기](revert-the-word-breakers-used-by-search-to-the-previous-version.md) </span><span class="sxs-lookup"><span data-stu-id="52107-178">[Revert the Word Breakers Used by Search to the Previous Version](revert-the-word-breakers-used-by-search-to-the-previous-version.md) </span></span>  
 [<span data-ttu-id="52107-179">전체 텍스트 검색의 동작 변경</span><span class="sxs-lookup"><span data-stu-id="52107-179">Behavior Changes to Full-Text Search</span></span>](full-text-search.md)  
  
  
