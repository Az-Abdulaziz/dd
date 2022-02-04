# Generating Permutation Algorithm

      using System;
      using System.Diagnostics;
      using System.Threading;
      using System.Collections.Generic;
      public class GFG
      {
          static void printArr(int[] a, int n)
          {
              for (int i = 0; i < n; i++)
                  Console.Write(a[i] + " ");
              Console.WriteLine();
          }
          static void heapPermutation(int[] a, int size, int n)
          {
              // if size becomes 1 then prints the obtained
              // permutation
              if (size == 1)
                  printArr(a, n);
              for (int i = 0; i < size; i++)
              {
                  heapPermutation(a, size - 1, n);
                  // if size is odd, swap 0th i.e (first) and
                  // (size-1)th i.e (last) element
                  if (size % 2 == 1)
                  {
                      int temp = a[0];
                      a[0] = a[size - 1];
                      a[size - 1] = temp;
                  }
                  // If size is even, swap ith and
                  // (size-1)th i.e (last) element
                  else
                  {
                      int temp = a[i];
                      a[i] = a[size - 1];
                      a[size - 1] = temp;
                  }
              }
          }
          public static void Main()
          {
              int[] a = new int[20];
              int[] v = new int[a.Length];
              Stopwatch sw = new Stopwatch();
              sw.Start();
              for (int i = 0; i < v.Length; i++)
              {
                  v[i] = i + 1;
              }
              Console.WriteLine("The number of Possibilities={0}",Fact(v.Length));
              heapPermutation(v, v.Length, v.Length);
              sw.Stop();
              Console.Write(" {0}",sw.Elapsed.TotalSeconds);
              Console.ReadKey();
          }
          public static int  Fact(int n)
          {
              if (n == 0)
                  return 1;
              else
                  return n * Fact(n-1);
          }

      } 
  
