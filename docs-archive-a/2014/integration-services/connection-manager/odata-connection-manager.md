---
title: OData 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 46eedaa008b284661fd1d364d2e2bc87c373a9f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652263"
---
# <a name="odata-connection-manager"></a><span data-ttu-id="0819c-102">OData 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="0819c-102">OData Connection Manager</span></span>
  <span data-ttu-id="0819c-103">OData 연결 관리자를 사용하면 패키지에서 OData 원본에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-103">An OData connection manager enables a package to connect to an OData source.</span></span> <span data-ttu-id="0819c-104">OData 원본 구성 요소는 OData 연결 관리자를 사용하여 OData 원본에 연결하고 서비스에서 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-104">An OData Source component connects to an OData source using an OData connection manager and consumes data from the service.</span></span> <span data-ttu-id="0819c-105">이러한 구성 요소 설치 지침을 비롯한 자세한 내용은 [OData Source](../data-flow/odata-source.md)섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0819c-105">See [OData Source](../data-flow/odata-source.md)section for detailed information including the installation instructions for these components.</span></span>  
  
## <a name="adding-connection-manager-to-an-ssis-package"></a><span data-ttu-id="0819c-106">SSIS 패키지에 연결 관리자 추가</span><span class="sxs-lookup"><span data-stu-id="0819c-106">Adding Connection Manager to an SSIS Package</span></span>  
 <span data-ttu-id="0819c-107">세 가지 방법으로 새로운 OData 연결 관리자를 SSIS 패키지에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-107">You can add a new OData Connection Manager to an SSIS package in three ways:</span></span>  
  
-   <span data-ttu-id="0819c-108">**OData 원본 편집기**에서 **새로 만들기...** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-108">Click the **New...** button in the **OData Source Editor**</span></span>  
  
-   <span data-ttu-id="0819c-109">**솔루션 탐색기** 에서 **연결 관리자** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 연결 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-109">Right-click **Connection Managers** folder in the **Solution Explorer** and click **New Connection Manager**.</span></span> <span data-ttu-id="0819c-110">**연결 관리자 유형** 에 대해 **ODATA**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-110">Select **ODATA** for **Connection manager type**.</span></span>  
  
-   <span data-ttu-id="0819c-111">패키지 디자이너 아래쪽에서 **연결 관리자** 창을 마우스 오른쪽 단추로 클릭 하 고 **새 연결**...을 선택 합니다. **연결 관리자 유형**에 대해 **ODATA** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-111">Right-click in the **Connection Managers** pane at the bottom of the package designer, and select **New Connection...**. Select **ODATA** for **Connection manager type**.</span></span>  
  
## <a name="connection-manager-authentication"></a><span data-ttu-id="0819c-112">연결 관리자 인증</span><span class="sxs-lookup"><span data-stu-id="0819c-112">Connection Manager Authentication</span></span>  
 <span data-ttu-id="0819c-113">OData 연결 관리자는 두 가지 모드의 인증을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-113">The OData Connection Manager supports two modes of authentication.</span></span>  
  
-   <span data-ttu-id="0819c-114">Windows 인증</span><span class="sxs-lookup"><span data-stu-id="0819c-114">Windows Authentication</span></span>  
  
-   <span data-ttu-id="0819c-115">기본 인증(사용자 이름/암호)</span><span class="sxs-lookup"><span data-stu-id="0819c-115">Basic Authentication (username/password)</span></span>  
  
 <span data-ttu-id="0819c-116">익명 액세스의 경우 Windows 인증 옵션을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="0819c-116">For anonymous access, select the Windows Authentication option</span></span>  
  
### <a name="specifying-and-securing-credentials"></a><span data-ttu-id="0819c-117">자격 증명 지정 및 보안</span><span class="sxs-lookup"><span data-stu-id="0819c-117">Specifying and Securing Credentials</span></span>  
 <span data-ttu-id="0819c-118">OData 서비스에 기본 인증이 필요한 경우 [OData Connection Manager Editor](../odata-connection-manager-editor.md)에서 사용자 이름과 암호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-118">If your OData service requires basic authentication, you can specify a username and password in the [OData Connection Manager Editor](../odata-connection-manager-editor.md).</span></span> <span data-ttu-id="0819c-119">편집기에 입력한 값은 패키지에서 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-119">The values you enter in the editor are persisted in the package.</span></span> <span data-ttu-id="0819c-120">암호 값은 패키지 보호 수준에 따라 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-120">The password value is encrypted according to the package protection level.</span></span>  
  
 <span data-ttu-id="0819c-121">사용자 이름 및 암호 값을 외부화/매개 변수화하는 여러 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-121">There are multiple ways to externalize/parameterize the username and password values.</span></span> <span data-ttu-id="0819c-122">[!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] 에서 이를 수행하는 두 가지 기본 방법은 매개 변수를 사용하거나, SQL Server Management Studio를 사용하여 패키지를 실행할 때 연결 관리자 속성을 직접 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-122">The two primary ways of doing this in [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] are by using parameters, or by setting the connection manager properties directly when you run the package using SQL Server Management Studio.</span></span>  
  
## <a name="odata-connection-manager-properties"></a><span data-ttu-id="0819c-123">OData 연결 관리자 속성</span><span class="sxs-lookup"><span data-stu-id="0819c-123">OData Connection Manager Properties</span></span>  
 <span data-ttu-id="0819c-124">다음 목록에서는 변경하려고 할 수 있는 몇 가지 OData 연결 관리자 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-124">The following list describes some of the OData Connection Manager properties that you may want to change.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0819c-125">속성</span><span class="sxs-lookup"><span data-stu-id="0819c-125">Property</span></span>|<span data-ttu-id="0819c-126">Description</span><span class="sxs-lookup"><span data-stu-id="0819c-126">Description</span></span>|  
|<span data-ttu-id="0819c-127">Url</span><span class="sxs-lookup"><span data-stu-id="0819c-127">Url</span></span>|<span data-ttu-id="0819c-128">서비스 문서에 대한 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-128">URL to the service document.</span></span>|  
|<span data-ttu-id="0819c-129">UserName</span><span class="sxs-lookup"><span data-stu-id="0819c-129">UserName</span></span>|<span data-ttu-id="0819c-130">기본 인증에 사용할 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-130">Username to use for Basic Authentication.</span></span>|  
|<span data-ttu-id="0819c-131">암호</span><span class="sxs-lookup"><span data-stu-id="0819c-131">Password</span></span>|<span data-ttu-id="0819c-132">기본 인증에 사용할 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-132">Password to use for Basic Authentication.</span></span>|  
|<span data-ttu-id="0819c-133">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="0819c-133">ConnectionString</span></span>|<span data-ttu-id="0819c-134">연결 관리자의 다른 속성을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="0819c-134">Reflects other properties of the connection manager.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0819c-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0819c-135">See Also</span></span>  
 [<span data-ttu-id="0819c-136">OData 연결 관리자 편집기</span><span class="sxs-lookup"><span data-stu-id="0819c-136">OData Connection Manager Editor</span></span>](../odata-connection-manager-editor.md)  
  
  
