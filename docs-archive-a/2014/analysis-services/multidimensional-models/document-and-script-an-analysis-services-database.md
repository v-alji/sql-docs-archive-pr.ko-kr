---
title: Analysis Services 데이터베이스 문서화 및 스크립팅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- XML for Analysis, scripts
- XMLA, scripts
- scripts [Analysis Services], databases
- documenting databases
- databases [Analysis Services], documenting
- databases [Analysis Services], scripts
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
author: minewiskan
ms.author: owend
ms.openlocfilehash: cfe008b0d6903d7d012eb57d41d6e50240202ec8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660160"
---
# <a name="document-and-script-an-analysis-services-database"></a><span data-ttu-id="d21c0-102">Analysis Services 데이터베이스 문서화 및 스크립트</span><span class="sxs-lookup"><span data-stu-id="d21c0-102">Document and Script an Analysis Services Database</span></span>
  <span data-ttu-id="d21c0-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스가 배포되면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 데이터베이스 또는 데이터베이스에 포함된 개체의 메타데이터를 XMLA(XML for Analysis) 스크립트로 출력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d21c0-103">After an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database is deployed, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to output the metadata of the database, or of an object contained in the database, as an XML for Analysis (XMLA) script.</span></span> <span data-ttu-id="d21c0-104">이 스크립트를 새로운 **XMLA 쿼리 편집기** 창, 파일 또는 클립보드로 출력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d21c0-104">You can output this script to a new **XMLA Query Editor** window, to a file, or to the Clipboard.</span></span> <span data-ttu-id="d21c0-105">XMLA에 대 한 자세한 내용은 [Analysis Services 스크립팅 언어 &#40;인&#41; 참조](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d21c0-105">For more information about XMLA, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>  
  
 <span data-ttu-id="d21c0-106">생성된 XMLA 스크립트는 ASSL( [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language) 요소를 사용하여 스크립트에 포함된 개체를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d21c0-106">The generated XMLA script uses [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) elements to define the objects contained by the script.</span></span> <span data-ttu-id="d21c0-107">CREATE 스크립트를 생성한 경우 결과 XMLA 스크립트는 인스턴스에서 전체 **데이터베이스 구조를 만드는 데 사용할 수 있는 XMLA** Create [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 명령과 ASSL 요소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d21c0-107">If you generated a CREATE script, the resulting XMLA script contains an XMLA **Create** command and ASSL elements that can be used to create the entire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database structure on an instance.</span></span> <span data-ttu-id="d21c0-108">ALTER 스크립트를 생성한 경우 결과 XMLA 스크립트는 기존 **데이터베이스 구조를 스크립트 생성 시의 데이터베이스 상태로 복원하는 데 사용할 수 있는 XMLA** Alter [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 명령과 ASSL 요소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d21c0-108">If you generated an ALTER script, the resulting XMLA script contains an XMLA **Alter** command and ASSL elements that can be used to restore the structure of an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database to the state of the database at the time the script was created.</span></span>  
  
 <span data-ttu-id="d21c0-109">생성된 XMLA 스크립트를 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에서 다음과 같은 방법으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d21c0-109">You can use the generated XMLA script from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in many ways, including:</span></span>  
  
-   <span data-ttu-id="d21c0-110">모든 데이터베이스 개체 및 사용 권한을 다시 만들 수 있는 백업 스크립트 유지 관리</span><span class="sxs-lookup"><span data-stu-id="d21c0-110">To maintain a backup script that allows you to recreate all the database objects and permissions.</span></span>  
  
-   <span data-ttu-id="d21c0-111">데이터베이스 개발 코드 만들기 또는 업데이트</span><span class="sxs-lookup"><span data-stu-id="d21c0-111">To create or update database development code.</span></span>  
  
-   <span data-ttu-id="d21c0-112">기존 스키마로부터 테스트 또는 개발 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="d21c0-112">To create a test or development environment from an existing schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d21c0-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d21c0-113">See Also</span></span>  
 <span data-ttu-id="d21c0-114">[Analysis Services 데이터베이스 수정 또는 삭제](modify-or-delete-an-analysis-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="d21c0-114">[Modify or Delete an Analysis Services Database](modify-or-delete-an-analysis-services-database.md) </span></span>  
 <span data-ttu-id="d21c0-115">[Alter Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="d21c0-115">[Alter Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) </span></span>  
 [<span data-ttu-id="d21c0-116">Create 요소&#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="d21c0-116">Create Element &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)  
  
  
