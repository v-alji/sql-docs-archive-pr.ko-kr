---
title: XMLA를 사용 하 여 모델 솔루션 배포 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- XML scripts [Analysis Services]
- scripts [Analysis Services], deployment
- deploying [Analysis Services], XML scripts
- Analysis Services deployments, XML scripts
ms.assetid: a8cb1837-fcac-4730-bea4-a72cf94d9f7c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b78490c5ab6ad3ba5e52bb82d4be254e3f5f102b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741404"
---
# <a name="deploy-model-solutions-using-xmla"></a><span data-ttu-id="fabe7-102">XMLA를 사용하여 모델 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="fabe7-102">Deploy Model Solutions Using XMLA</span></span>
  <span data-ttu-id="fabe7-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 **데이터베이스 스크립팅** 명령의 **CREATE** 옵션은 전체 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 또는 해당 구성 개체 중 하나에 대해 XML 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fabe7-103">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], the **CREATE To** option of the **Script Database As** command creates an XML script of an entire [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or one of its constituent objects.</span></span> <span data-ttu-id="fabe7-104">그런 다음 결과로 얻은 스크립트를 다른 컴퓨터에서 실행하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스의 스키마(메타데이터)를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fabe7-104">The resulting script can then be run on another computer to recreate the schema (metadata) of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="fabe7-105">이 스크립트는 전체 데이터베이스를 생성합니다. 스크립트 사용 시 이미 배포된 개체를 증분 업데이트하는 메커니즘은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fabe7-105">The script generates the entire database, and there is no mechanism for incrementally updating already deployed objects when using the script.</span></span> <span data-ttu-id="fabe7-106">스크립트를 실행하고 데이터베이스를 배포한 후에는 새로 만든 데이터베이스를 처리해야만 사용자가 해당 데이터베이스를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fabe7-106">After running the script and deploying the database, the newly created database must be processed before users can browse it.</span></span>  
  
 <span data-ttu-id="fabe7-107">**데이터베이스 스크립팅** 명령에 대한 자세한 내용은 [Analysis Services 데이터베이스 문서화 및 스크립트](document-and-script-an-analysis-services-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fabe7-107">For more information about the **Script Database As** command, see [Document and Script an Analysis Services Database](document-and-script-an-analysis-services-database.md).</span></span>  
  
## <a name="modifying-object-properties-in-the-xml-script"></a><span data-ttu-id="fabe7-108">XML 스크립트에서 개체 속성 수정</span><span class="sxs-lookup"><span data-stu-id="fabe7-108">Modifying Object Properties in the XML Script</span></span>  
 <span data-ttu-id="fabe7-109">**데이터베이스 스크립팅** 명령을 사용할 때는 데이터베이스 이름, 데이터 원본 연결 문자열 및 보안 설정과 같은 데이터베이스 개체의 특정 속성을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fabe7-109">When using the **Script Database As** command, you cannot modify specific properties (such as the database name, data source connection strings, and security settings) of the database objects.</span></span> <span data-ttu-id="fabe7-110">이러한 속성은 스크립트를 실행한 후 배포된 데이터베이스에서 스크립트가 생성되거나 수정된 이후에 해당 스크립트에서 수동으로 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fabe7-110">These properties must either be manually modified in the script after the script has been generated or modified in the deployed database after running the script.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fabe7-111">XML 스크립트가 데이터 원본이나 가장 용도의 연결 문자열에 지정된 경우 암호가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fabe7-111">The XML script will not contain the password if this is specified in either the connection string for a data source or for impersonation purposes.</span></span> <span data-ttu-id="fabe7-112">이 시나리오에서는 처리 용도로 암호가 필요하기 때문에 XML 스크립트가 실행되기 전에 또는 XML 스크립트가 실행된 후에 해당 스크립트에 직접 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fabe7-112">Since the password is required for processing purposes in this scenario, you will either need to add this manually to the XML script before it executes or add it after the XML script executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fabe7-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fabe7-113">See Also</span></span>  
 <span data-ttu-id="fabe7-114">[배포 마법사를 사용 하 여 모델 솔루션 배포](deploy-model-solutions-using-the-deployment-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="fabe7-114">[Deploy Model Solutions Using the Deployment Wizard](deploy-model-solutions-using-the-deployment-wizard.md) </span></span>  
 [<span data-ttu-id="fabe7-115">Analysis Services 데이터베이스 동기화</span><span class="sxs-lookup"><span data-stu-id="fabe7-115">Synchronize Analysis Services Databases</span></span>](synchronize-analysis-services-databases.md)  
  
  
