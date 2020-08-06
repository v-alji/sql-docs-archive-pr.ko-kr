---
title: CDC Service 명령줄 인터페이스를 사용하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab87b7da-c3b9-4bc8-a853-798716cbf74b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78226e603795c8c9ed4f7129a8abf0b57b29083c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727304"
---
# <a name="how-to-use-the-cdc-service-command-line-interface"></a><span data-ttu-id="35b39-102">CDC Service 명령줄 인터페이스를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="35b39-102">How to Use the CDC Service Command-Line Interface</span></span>
  <span data-ttu-id="35b39-103">Oracle CDC Service 프로그램인 xdbcdcsvc.exe는 일반적으로 Oracle CDC Windows 서비스를 실행하지만 명령줄에서 직접 이 프로그램을 호출하여 Oracle CDC Windows 서비스를 만들거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35b39-103">The Oracle CDC service program, xdbcdcsvc.exe, normally runs the Oracle CDC Windows service but it can be invoked directly from the command line to create, or delete an Oracle CDC Windows service.</span></span>  
  
### <a name="to-use-the-command-line"></a><span data-ttu-id="35b39-104">명령줄을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="35b39-104">To use the command line</span></span>  
  
1.  <span data-ttu-id="35b39-105">**시작** 메뉴에서 명령줄 콘솔을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="35b39-105">From the **Start** menu, open the command-line console.</span></span> <span data-ttu-id="35b39-106">실행 또는 검색 상자에 **cmd** 를 입력하여 콘솔을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="35b39-106">Type **cmd** in the run or search box to open the console.</span></span>  
  
2.  <span data-ttu-id="35b39-107">명령 프롬프트에 **cd** 를 입력하고 Oracle CDC Service가 설치되는 폴더의 전체 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="35b39-107">At the command prompt, type **cd** and the full path to the folder where the CDC Service for Oracle is installed.</span></span>  
  
3.  <span data-ttu-id="35b39-108">가능한 태스크 중 하나를 수행하는 데 필요한 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="35b39-108">Type the command that you need to carry out one of the possible tasks.</span></span>  
  
  
