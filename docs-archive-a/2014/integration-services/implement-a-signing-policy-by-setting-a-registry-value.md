---
title: 레지스트리 값을 설정 하 여 서명 정책을 구현 합니다. Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- signing policies [Integration Services]
ms.assetid: 64f6966f-2292-401f-acb1-2ccb5aee484a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1e844b65df5b45f212554f7583f4e4b327b740e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647119"
---
# <a name="implement-a-signing-policy-by-setting-a-registry-value"></a><span data-ttu-id="c22c0-102">레지스트리 값을 설정하여 서명 정책 구현</span><span class="sxs-lookup"><span data-stu-id="c22c0-102">Implement a Signing Policy by Setting a Registry Value</span></span>
  <span data-ttu-id="c22c0-103">선택적 레지스트리 값을 사용하여 서명된 패키지나 서명되지 않은 패키지를 로드하기 위한 조직의 정책을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-103">You can use an optional registry value to manage an organization's policy for loading signed or unsigned packages.</span></span> <span data-ttu-id="c22c0-104">이 레지스트리 값을 사용하면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 실행하고 정책을 적용할 각 컴퓨터에 이 레지스트리 값을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-104">If you use this registry value, you must create this registry value on each computer on which [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages will run and on which you want to enforce the policy.</span></span> <span data-ttu-id="c22c0-105">레지스트리 값이 설정된 후 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 는 패키지를 로드하기 전에 서명을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-105">After the registry value has been set, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] will check or verify the signatures before loading packages.</span></span>  
  
 <span data-ttu-id="c22c0-106">이 항목의 절차에서는 선택적 `BlockedSignatureStates` DWORD 값을 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS 레지스트리 키에 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-106">This procedure in this topic describes how to add the optional `BlockedSignatureStates` DWORD value to the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS registry key.</span></span> <span data-ttu-id="c22c0-107">`BlockedSignatureStates`의 데이터 값은 패키지에 신뢰할 수 없는 서명이나 잘못된 서명이 있거나 패키지가 서명되지 않은 경우에 패키지를 차단해야 하는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-107">The data value in `BlockedSignatureStates` determines whether a package should be blocked if it has an untrusted signature, has an invalid signature, or is unsigned.</span></span> <span data-ttu-id="c22c0-108">패키지 서명에 사용되는 서명 상태와 관련해서 `BlockedSignatureStates` 레지스트리 값은 다음 정의를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-108">With regard to the status of signatures used to sign packages, the `BlockedSignatureStates` registry value uses the following definitions:</span></span>  
  
-   <span data-ttu-id="c22c0-109">*유효한 서명* 이란 성공적으로 읽을 수 있는 서명을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-109">A *valid signature* is one that can be read successfully.</span></span>  
  
-   <span data-ttu-id="c22c0-110">*잘못된 서명* 이란 해독된 체크섬(프라이빗 키로 암호화된 패키지 코드의 단방향 해시)이 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 로드하는 과정에 계산하여 해독된 체크섬과 일치하지 않는 서명을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-110">An *invalid signature* is one for which the decrypted checksum (the one-way hash of the package code encrypted by a private key) does not match the decrypted checksum that is calculated as part of the process of loading [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>  
  
-   <span data-ttu-id="c22c0-111">*신뢰할 수 있는 서명* 이란 신뢰할 수 있는 루트 인증 기관에서 서명한 디지털 인증서를 사용하여 만든 서명을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-111">A *trusted signature* is one that is created by using a digital certificate signed by a Trusted Root Certification Authority.</span></span> <span data-ttu-id="c22c0-112">이 설정을 사용할 경우 서명자가 사용자의 신뢰할 수 있는 게시자 목록에 없어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-112">This setting does not require the signer to be found in the user's list of Trusted Publishers.</span></span>  
  
-   <span data-ttu-id="c22c0-113">*신뢰할 수 없는 서명* 이란 신뢰할 수 있는 루트 인증 기관에서 발급되었는지 확인할 수 없거나 최신 상태가 아닌 서명을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-113">An *untrusted signature* is one that cannot be verified as issued by a Trusted Root Certification Authority, or a signature that is not current.</span></span>  
  
 <span data-ttu-id="c22c0-114">다음 표에서는 DWORD 데이터의 유효한 값 및 연관된 정책을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-114">The following table lists the valid values of the DWORD data and their associated policy.</span></span>  
  
|<span data-ttu-id="c22c0-115">값</span><span class="sxs-lookup"><span data-stu-id="c22c0-115">Value</span></span>|<span data-ttu-id="c22c0-116">Description</span><span class="sxs-lookup"><span data-stu-id="c22c0-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c22c0-117">0</span><span class="sxs-lookup"><span data-stu-id="c22c0-117">0</span></span>|<span data-ttu-id="c22c0-118">관리 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-118">No administrative restriction.</span></span>|  
|<span data-ttu-id="c22c0-119">1</span><span class="sxs-lookup"><span data-stu-id="c22c0-119">1</span></span>|<span data-ttu-id="c22c0-120">잘못된 서명을 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-120">Block invalid signatures.</span></span><br /><br /> <span data-ttu-id="c22c0-121">이 설정은 서명되지 않은 패키지를 차단하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-121">This setting does not block unsigned packages.</span></span>|  
|<span data-ttu-id="c22c0-122">2</span><span class="sxs-lookup"><span data-stu-id="c22c0-122">2</span></span>|<span data-ttu-id="c22c0-123">잘못된 서명과 신뢰할 수 없는 서명을 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-123">Block invalid and untrusted signatures.</span></span><br /><br /> <span data-ttu-id="c22c0-124">이 설정은 서명되지 않은 패키지를 차단하지 않지만 자체 생성된 서명은 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-124">This setting does not block unsigned packages, but blocks self-generated signatures.</span></span>|  
|<span data-ttu-id="c22c0-125">3</span><span class="sxs-lookup"><span data-stu-id="c22c0-125">3</span></span>|<span data-ttu-id="c22c0-126">잘못된 서명과 신뢰할 수 없는 서명, 서명되지 않은 패키지를 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-126">Block invalid and untrusted signatures and unsigned packages</span></span><br /><br /> <span data-ttu-id="c22c0-127">이 설정은 자체 생성된 서명도 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-127">This setting also blocks self-generated signatures.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="c22c0-128">`BlockedSignatureStates`에 대한 권장 설정은 3입니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-128">The recommended setting for `BlockedSignatureStates` is 3.</span></span> <span data-ttu-id="c22c0-129">이 설정은 서명되지 않은 패키지나 잘못된 서명 또는 신뢰할 수 없는 서명에 대해 가장 강력한 보호 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-129">This setting provides the greatest protection against unsigned packages or signatures that are either not valid or untrusted.</span></span> <span data-ttu-id="c22c0-130">그러나 권장 설정이 모든 경우에 적합하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-130">However, the recommended setting may not be appropriate in all circumstances.</span></span> <span data-ttu-id="c22c0-131">디지털 자산에 서명하는 방법은 MSDN Library에서 "[코드 서명 소개(Introduction to Code Signing)](https://go.microsoft.com/fwlink/?LinkId=51414)" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c22c0-131">For more information about signing digital assets, see the topic, "[Introduction to Code Signing](https://go.microsoft.com/fwlink/?LinkId=51414)," in the MSDN Library.</span></span>  
  
### <a name="to-implement-a-signing-policy-for-packages"></a><span data-ttu-id="c22c0-132">패키지에 대한 서명 정책을 구현하려면</span><span class="sxs-lookup"><span data-stu-id="c22c0-132">To implement a signing policy for packages</span></span>  
  
1.  <span data-ttu-id="c22c0-133">**시작** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-133">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="c22c0-134">실행 대화 상자에서를 입력 한 `Regedit` 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-134">In the Run dialog box, type `Regedit`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="c22c0-135">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS 레지스트리 키를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-135">Locate the registry key, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS.</span></span>  
  
4.  <span data-ttu-id="c22c0-136">**MSDTS**를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 다음 **DWORD 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-136">Right-click **MSDTS**, point to **New**, and then click **DWORD Value**.</span></span>  
  
5.  <span data-ttu-id="c22c0-137">새 값의 이름을 `BlockedSignatureStates`(으)로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-137">Update the name of the new value to `BlockedSignatureStates`.</span></span>  
  
6.  <span data-ttu-id="c22c0-138">마우스 오른쪽 단추 `BlockedSignatureStates` 를 클릭 하 고 **수정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-138">Right-click `BlockedSignatureStates` and click **Modify**.</span></span>  
  
7.  <span data-ttu-id="c22c0-139">**DWORD 값 편집** 대화 상자에서 값 0, 1, 2 또는 3을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-139">In the **Edit DWORD Value** dialog box, type the value 0, 1, 2, or 3.</span></span>  
  
8.  <span data-ttu-id="c22c0-140">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-140">Click **OK**.</span></span>  
  
9. <span data-ttu-id="c22c0-141">**파일** 메뉴에서 **끝내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c22c0-141">On the **File** menu, click **Exit**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c22c0-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c22c0-142">See Also</span></span>  
 <span data-ttu-id="c22c0-143">[보안 개요 &#40;Integration Services&#41;](security/security-overview-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="c22c0-143">[Security Overview &#40;Integration Services&#41;](security/security-overview-integration-services.md) </span></span>  
 [<span data-ttu-id="c22c0-144">디지털 서명을 사용하여 패키지 원본 확인</span><span class="sxs-lookup"><span data-stu-id="c22c0-144">Identify the Source of Packages with Digital Signatures</span></span>](security/identify-the-source-of-packages-with-digital-signatures.md)  
  
  
