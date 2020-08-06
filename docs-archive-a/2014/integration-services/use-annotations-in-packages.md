---
title: 패키지에서 주석 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- self-documenting packages
- adding annotations
- annotations [Integration Services]
ms.assetid: 48c8ed9a-b10d-490c-9ba7-4b77aa44e3dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 27c7df6afd894ea9730027da1d54786ed8397fad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661713"
---
# <a name="use-annotations-in-packages"></a><span data-ttu-id="86769-102">패키지에서 주석 사용</span><span class="sxs-lookup"><span data-stu-id="86769-102">Use Annotations in Packages</span></span>
  <span data-ttu-id="86769-103">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너는 패키지에 대한 설명을 제공하고 이해 및 유지 관리를 쉽게 하기 위해 사용할 수 있는 주석을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="86769-103">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer provides annotations, which you can use to make packages self-documenting and easier to understand and maintain.</span></span> <span data-ttu-id="86769-104">주석은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너의 제어 흐름, 데이터 흐름 및 이벤트 처리기에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86769-104">You can add annotations to the control flow, data flow, and event handler design surfaces of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="86769-105">주석에는 모든 종류의 텍스트가 포함될 수 있으며 패키지에 레이블, 설명 및 기타 설명 정보를 추가하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="86769-105">The annotations can contain any type of text, and they are useful for adding labels, comments, and other descriptive information to a package.</span></span> <span data-ttu-id="86769-106">주석은 디자인 타임 전용 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="86769-106">Annotations are a design-time feature only.</span></span> <span data-ttu-id="86769-107">예를 들어 주석은 로그에 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86769-107">For example, they are not written to logs.</span></span>  
  
 <span data-ttu-id="86769-108">Enter 키를 누르면 텍스트가 다음 줄로 줄 바꿈됩니다.</span><span class="sxs-lookup"><span data-stu-id="86769-108">When you press ENTER, the text wraps to the next line.</span></span> <span data-ttu-id="86769-109">텍스트 줄을 추가하면 주석 상자의 크기가 자동으로 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="86769-109">The annotation box automatically increases in size as you add additional lines of text.</span></span> <span data-ttu-id="86769-110">패키지 파일의 CDATA 섹션에 있는 패키지 주석은 일반 텍스트로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="86769-110">Package annotations are persisted as clear text in the CDATA section of the package file.</span></span>  
  
 <span data-ttu-id="86769-111">패키지 파일의 형식을 변경하는 방법에 대한 자세한 내용은 [SSIS 패키지 형식](../../2014/integration-services/ssis-package-format.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86769-111">For more information about changes to the format of the package file, see [SSIS Package Format](../../2014/integration-services/ssis-package-format.md).</span></span>  
  
 <span data-ttu-id="86769-112">패키지가 저장될 때 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너는 주석을 해당 패키지에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="86769-112">When you save the package, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer saves the annotations in the package.</span></span>  
  
### <a name="to-add-an-annotation-to-a-package"></a><span data-ttu-id="86769-113">패키지에 주석을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="86769-113">To add an annotation to a package</span></span>  
  
-   [<span data-ttu-id="86769-114">패키지에 주석 추가</span><span class="sxs-lookup"><span data-stu-id="86769-114">Add an Annotation to a Package</span></span>](../../2014/integration-services/add-an-annotation-to-a-package.md)  
  
  
