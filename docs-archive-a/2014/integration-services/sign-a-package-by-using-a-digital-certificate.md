---
title: 디지털 인증서를 사용 하 여 패키지 서명 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- digital signatures [Integration Services]
- signing packages [Integration Services]
- signatures [Integration Services]
ms.assetid: 182b115e-0fe2-4717-8dff-183f9eb6e397
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6bd0f73d609623f882e474c96a01cd3bc0274b6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742359"
---
# <a name="sign-a-package-by-using-a-digital-certificate"></a><span data-ttu-id="74a1b-102">디지털 인증서를 사용하여 패키지 서명</span><span class="sxs-lookup"><span data-stu-id="74a1b-102">Sign a Package by Using a Digital Certificate</span></span>
  <span data-ttu-id="74a1b-103">이 항목에서는 디지털 인증서를 사용하여 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지에 서명하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-103">This topic describes how to sign an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package with a digital certificate.</span></span> <span data-ttu-id="74a1b-104">디지털 서명을 다른 설정과 함께 사용하여 잘못된 패키지를 로드하거나 실행하지 못하게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-104">You can use a digital signature, together with other settings, to prevent a package that is not valid from loading and running.</span></span>  
  
 <span data-ttu-id="74a1b-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지에 서명하려면 먼저 다음 태스크를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-105">Before you can sign an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, you must do the following tasks:</span></span>  
  
-   <span data-ttu-id="74a1b-106">인증서와 연결할 프라이빗 키를 만들거나 가져오고 이 프라이빗 키를 로컬 컴퓨터에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-106">Create or obtain a private key to associate with the certificate, and store this private key on the local computer.</span></span>  
  
-   <span data-ttu-id="74a1b-107">신뢰할 수 인증 기관에서 코드 서명에 사용할 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-107">Obtain a certificate for the purpose of code signing from a trusted certification authority.</span></span> <span data-ttu-id="74a1b-108">다음 방법 중 하나를 사용하여 인증서를 가져오거나 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-108">You can use one of the following methods to obtain or create a certificate:</span></span>  
  
    -   <span data-ttu-id="74a1b-109">인증서를 발급하는 상업적 공용 인증 기관에서 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-109">Obtain a certificate from a public, commercial certification authority that issues certificates.</span></span>  
  
    -   <span data-ttu-id="74a1b-110">조직에서 내부적으로 인증서를 발급할 수 있도록 인증서 서버에서 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-110">Obtain a certificate from a certificate server, that enables an organization to internally issue certificates.</span></span> <span data-ttu-id="74a1b-111">인증서에 서명하는 데 사용하는 루트 인증서를 **신뢰할 수 있는 루트 인증 기관** 저장소에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-111">You have to add the root certificate that is used to sign the certificate to the **Trusted Root Certification Authorities** store.</span></span> <span data-ttu-id="74a1b-112">루트 인증서를 추가하려면 MMC( [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console)에 대한 인증서 스냅인을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-112">To add the root certificate, you can use the Certificates snap-in for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console (MMC).</span></span> <span data-ttu-id="74a1b-113">자세한 내용은 MSDN Library에서 "[Certificate Services](https://go.microsoft.com/fwlink/?LinkId=100755)" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="74a1b-113">For more information, see the topic, "[Certificate Services](https://go.microsoft.com/fwlink/?LinkId=100755)," in the MSDN library.</span></span>  
  
    -   <span data-ttu-id="74a1b-114">테스트용으로만 사용할 자체의 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-114">Create your own certificate for testing purposes only.</span></span> <span data-ttu-id="74a1b-115">인증서 작성 도구(Makecert.exe)를 사용하면 테스트용 X.509 인증서를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-115">The Certificate Creation Tool (Makecert.exe) generates X.509 certificates for testing purposes.</span></span> <span data-ttu-id="74a1b-116">자세한 내용은 MSDN Library에서 "[인증서 작성 도구(Makecert.exe)](https://go.microsoft.com/fwlink/?LinkId=100756)" 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74a1b-116">For more information, see the topic, "[Certificate Creation Tool (Makecert.exe)](https://go.microsoft.com/fwlink/?LinkId=100756)," in the MSDN Library.</span></span>  
  
     <span data-ttu-id="74a1b-117">인증서에 대한 자세한 내용은 인증서 스냅인의 온라인 도움말을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="74a1b-117">For more information about certificates, see the online Help for the Certificates snap-in.</span></span> <span data-ttu-id="74a1b-118">디지털 자산에 서명하는 방법에 대한 자세한 내용은 MSDN Library에서 "[Signing and Checking Code with Authenticode](https://go.microsoft.com/fwlink/?LinkId=78100)" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="74a1b-118">For more information about how to sign digital assets, see the topic, "[Signing and Checking Code with Authenticode](https://go.microsoft.com/fwlink/?LinkId=78100)," in the MSDN Library.</span></span>  
  
-   <span data-ttu-id="74a1b-119">인증서를 코드 서명에 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-119">Make sure that the certificate has been enabled for code signing.</span></span> <span data-ttu-id="74a1b-120">코드 서명에 인증서를 사용할 수 있는지 여부를 확인하려면 인증서 스냅인에서 인증서 속성을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-120">To determine whether a certificate is enabled for code signing, review the properties of the certificate in the Certificates snap-in.</span></span>  
  
-   <span data-ttu-id="74a1b-121">인증서를 개인 저장소에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-121">Store the certificate in the Personal store.</span></span>  
  
 <span data-ttu-id="74a1b-122">위의 태스크를 완료한 후 다음 절차에 따라 패키지에 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-122">After you have completed the previous tasks, you can use the following procedure to sign a package.</span></span>  
  
### <a name="to-sign-a-package"></a><span data-ttu-id="74a1b-123">패키지에 서명하려면</span><span class="sxs-lookup"><span data-stu-id="74a1b-123">To sign a package</span></span>  
  
1.  <span data-ttu-id="74a1b-124">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 서명할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-124">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to be signed.</span></span>  
  
2.  <span data-ttu-id="74a1b-125">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-125">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="74a1b-126">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너의 **SSIS** 메뉴에서 **디지털 서명**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-126">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, on the **SSIS** menu, click **Digital Signing**.</span></span>  
  
4.  <span data-ttu-id="74a1b-127">**디지털 서명** 대화 상자에서 **서명**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-127">In the **Digital Signing** dialog box, click **Sign**.</span></span>  
  
5.  <span data-ttu-id="74a1b-128">**인증서 선택** 대화 상자에서 인증서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-128">In the **Select a Certificate** dialog box, select a certificate.</span></span>  
  
6.  <span data-ttu-id="74a1b-129">필요에 따라 **인증서 보기**를 클릭하여 인증서 정보를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-129">(Optional) Click **View Certificat**e to view certificate information.</span></span>  
  
7.  <span data-ttu-id="74a1b-130">**확인** 을 클릭하여 **인증서 선택** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-130">Click **OK** to close the **Select a Certificate** dialog box.</span></span>  
  
8.  <span data-ttu-id="74a1b-131">**확인** 을 클릭하여 **디지털 서명** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-131">Click **OK** to close the **Digital Signing** dialog box.</span></span>  
  
9. <span data-ttu-id="74a1b-132">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-132">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
     <span data-ttu-id="74a1b-133">패키지에 서명했더라도 패키지를 로드하기 전에 디지털 서명을 확인하도록 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a1b-133">Although the package has been signed, you must now configure [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] to check or verify the digital signature before loading the package.</span></span> <span data-ttu-id="74a1b-134">자세한 내용은 [디지털 서명을 사용하여 패키지 원본 확인](security/identify-the-source-of-packages-with-digital-signatures.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74a1b-134">For more information, see [Identify the Source of Packages with Digital Signatures](security/identify-the-source-of-packages-with-digital-signatures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a1b-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74a1b-135">See Also</span></span>  
 [<span data-ttu-id="74a1b-136">보안 개요&#40;Integration Services&#41;</span><span class="sxs-lookup"><span data-stu-id="74a1b-136">Security Overview &#40;Integration Services&#41;</span></span>](security/security-overview-integration-services.md)  
  
  
